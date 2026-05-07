import React, { useState, useEffect } from 'react';
import { 
  Plus, 
  Gamepad2, 
  ExternalLink, 
  Trash2, 
  Moon, 
  Sun, 
  LayoutGrid, 
  Info, 
  X,
  PlusCircle,
  Monitor
} from 'lucide-react';
import { initializeApp } from 'firebase/app';
import { 
  getFirestore, 
  collection, 
  addDoc, 
  onSnapshot, 
  deleteDoc, 
  doc, 
  query,
  updateDoc
} from 'firebase/firestore';
import { 
  getAuth, 
  signInAnonymously, 
  signInWithCustomToken, 
  onAuthStateChanged 
} from 'firebase/auth';

// --- Firebase Configuration ---
const firebaseConfig = JSON.parse(__firebase_config);
const app = initializeApp(firebaseConfig);
const auth = getAuth(app);
const db = getFirestore(app);
const appId = typeof __app_id !== 'undefined' ? __app_id : 'vibe-games-portfolio';

const App = () => {
  const [user, setUser] = useState(null);
  const [games, setGames] = useState([]);
  const [isDarkMode, setIsDarkMode] = useState(true);
  const [isModalOpen, setIsModalOpen] = useState(false);
  const [isLoading, setIsLoading] = useState(true);

  // Form State
  const [newGame, setNewGame] = useState({
    title: '',
    url: '',
    description: '',
    thumbnail: ''
  });

  // Auth initialization
  useEffect(() => {
    const initAuth = async () => {
      try {
        if (typeof __initial_auth_token !== 'undefined' && __initial_auth_token) {
          await signInWithCustomToken(auth, __initial_auth_token);
        } else {
          await signInAnonymously(auth);
        }
      } catch (error) {
        console.error("Auth error:", error);
      }
    };
    initAuth();
    const unsubscribe = onAuthStateChanged(auth, (user) => {
      setUser(user);
    });
    return () => unsubscribe();
  }, []);

  // Data Fetching
  useEffect(() => {
    if (!user) return;

    const gamesRef = collection(db, 'artifacts', appId, 'public', 'data', 'games');
    const unsubscribe = onSnapshot(gamesRef, 
      (snapshot) => {
        const gamesData = snapshot.docs.map(doc => ({
          id: doc.id,
          ...doc.data()
        }));
        // Sort in memory by creation time (Rule 2: No complex queries)
        setGames(gamesData.sort((a, b) => new Date(b.createdAt) - new Date(a.createdAt)));
        setIsLoading(false);
      },
      (error) => {
        console.error("Firestore error:", error);
        setIsLoading(false);
      }
    );

    return () => unsubscribe();
  }, [user]);

  const toggleDarkMode = () => setIsDarkMode(!isDarkMode);

  const handleInputChange = (e) => {
    const { name, value } = e.target;
    setNewGame(prev => ({ ...prev, [name]: value }));
  };

  const handleAddGame = async (e) => {
    e.preventDefault();
    if (!user) return;
    if (!newGame.title || !newGame.url) return;

    try {
      const gamesRef = collection(db, 'artifacts', appId, 'public', 'data', 'games');
      await addDoc(gamesRef, {
        ...newGame,
        createdAt: new Date().toISOString()
      });
      setNewGame({ title: '', url: '', description: '', thumbnail: '' });
      setIsModalOpen(false);
    } catch (error) {
      console.error("Add error:", error);
    }
  };

  const handleDeleteGame = async (id) => {
    if (!user) return;
    // Note: No native alert, using window.confirm as it's allowed for simple confirmations 
    // but better to use a custom modal if needed.
    if (window.confirm("정말로 이 게임을 삭제하시겠습니까?")) {
      try {
        await deleteDoc(doc(db, 'artifacts', appId, 'public', 'data', 'games', id));
      } catch (error) {
        console.error("Delete error:", error);
      }
    }
  };

  return (
    <div className={`min-h-screen transition-colors duration-300 ${isDarkMode ? 'bg-slate-950 text-slate-100' : 'bg-slate-50 text-slate-900'}`}>
      
      {/* Header */}
      <header className={`sticky top-0 z-40 w-full border-b backdrop-blur-md ${isDarkMode ? 'border-slate-800 bg-slate-950/80' : 'border-slate-200 bg-white/80'}`}>
        <div className="container mx-auto px-6 h-20 flex items-center justify-between">
          <div className="flex items-center gap-3">
            <div className="p-2 bg-indigo-600 rounded-xl">
              <Gamepad2 className="text-white w-6 h-6" />
            </div>
            <h1 className="text-2xl font-bold tracking-tight">Vibe Coding <span className="text-indigo-500">Portfolio</span></h1>
          </div>
          
          <div className="flex items-center gap-4">
            <button 
              onClick={toggleDarkMode}
              className={`p-2.5 rounded-full transition-all ${isDarkMode ? 'bg-slate-800 hover:bg-slate-700' : 'bg-slate-200 hover:bg-slate-300'}`}
              aria-label="Toggle dark mode"
            >
              {isDarkMode ? <Sun size={20} /> : <Moon size={20} />}
            </button>
            <button 
              onClick={() => setIsModalOpen(true)}
              className="hidden md:flex items-center gap-2 bg-indigo-600 hover:bg-indigo-500 text-white px-5 py-2.5 rounded-xl font-medium transition-all shadow-lg shadow-indigo-500/20"
            >
              <Plus size={20} /> 게임 추가하기
            </button>
            <button 
              onClick={() => setIsModalOpen(true)}
              className="md:hidden p-2.5 bg-indigo-600 text-white rounded-full"
            >
              <Plus size={20} />
            </button>
          </div>
        </div>
      </header>

      {/* Main Content */}
      <main className="container mx-auto px-6 py-12">
        {/* Intro Section */}
        <section className="mb-16 text-center max-w-2xl mx-auto">
          <h2 className="text-4xl md:text-5xl font-extrabold mb-6 tracking-tight">VIBE CODING GAMES</h2>
          <p className={`text-lg font-medium ${isDarkMode ? 'text-slate-400' : 'text-slate-600'}`}>
            모든 게임들은 Gemini를 이용하여 만들었습니다.
          </p>
        </section>

        {/* Game Grid */}
        {isLoading ? (
          <div className="flex justify-center items-center h-64">
            <div className="animate-spin rounded-full h-12 w-12 border-t-2 border-b-2 border-indigo-500"></div>
          </div>
        ) : games.length === 0 ? (
          <div className={`flex flex-col items-center justify-center py-20 px-6 border-2 border-dashed rounded-3xl ${isDarkMode ? 'border-slate-800 bg-slate-900/50' : 'border-slate-200 bg-slate-100/50'}`}>
            <LayoutGrid className="w-16 h-16 text-slate-500 mb-4 opacity-50" />
            <h3 className="text-xl font-semibold mb-2">아직 등록된 게임이 없습니다.</h3>
            <p className="text-slate-500 mb-6">첫 번째 게임을 추가하여 포트폴리오를 시작해 보세요!</p>
            <button 
              onClick={() => setIsModalOpen(true)}
              className="flex items-center gap-2 bg-indigo-600 hover:bg-indigo-500 text-white px-6 py-3 rounded-xl font-bold transition-all"
            >
              <PlusCircle size={20} /> 지금 추가하기
            </button>
          </div>
        ) : (
          <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
            {games.map((game) => (
              <div 
                key={game.id} 
                className={`group relative overflow-hidden rounded-3xl border transition-all duration-300 hover:-translate-y-2 hover:shadow-2xl ${
                  isDarkMode 
                  ? 'bg-slate-900 border-slate-800 hover:shadow-indigo-500/10' 
                  : 'bg-white border-slate-200 hover:shadow-slate-300/50'
                }`}
              >
                {/* Thumbnail */}
                <div className="aspect-video w-full overflow-hidden bg-slate-800 relative">
                  {game.thumbnail ? (
                    <img 
                      src={game.thumbnail} 
                      alt={game.title} 
                      className="w-full h-full object-cover transition-transform duration-500 group-hover:scale-110"
                      onError={(e) => { e.target.src = "https://images.unsplash.com/photo-1550745165-9bc0b252726f?auto=format&fit=crop&q=80&w=800"; }}
                    />
                  ) : (
                    <div className="w-full h-full flex items-center justify-center bg-gradient-to-br from-indigo-900 to-slate-900">
                      <Gamepad2 className="w-16 h-16 text-white/20" />
                    </div>
                  )}
                  <div className="absolute top-4 right-4 flex gap-2 translate-y-[-50px] opacity-0 group-hover:translate-y-0 group-hover:opacity-100 transition-all duration-300">
                    <button 
                      onClick={() => handleDeleteGame(game.id)}
                      className="p-2 bg-red-500/90 hover:bg-red-600 text-white rounded-lg backdrop-blur-sm shadow-lg"
                      title="삭제"
                    >
                      <Trash2 size={16} />
                    </button>
                  </div>
                </div>

                {/* Content */}
                <div className="p-6">
                  <h3 className="text-xl font-bold mb-2 group-hover:text-indigo-500 transition-colors">{game.title}</h3>
                  <p className={`text-sm mb-6 line-clamp-2 ${isDarkMode ? 'text-slate-400' : 'text-slate-600'}`}>
                    {game.description || '설명이 없습니다.'}
                  </p>
                  
                  <div className="flex items-center justify-between">
                    <a 
                      href={game.url} 
                      target="_blank" 
                      rel="noopener noreferrer"
                      className={`flex items-center gap-2 text-sm font-bold transition-all px-4 py-2 rounded-lg ${
                        isDarkMode 
                        ? 'bg-indigo-600/10 text-indigo-400 hover:bg-indigo-600 hover:text-white' 
                        : 'bg-indigo-100 text-indigo-600 hover:bg-indigo-600 hover:text-white'
                      }`}
                    >
                      <Monitor size={16} /> 플레이하기
                    </a>
                    <a 
                      href={game.url} 
                      target="_blank" 
                      rel="noopener noreferrer"
                      className="p-2 text-slate-500 hover:text-indigo-500 transition-colors"
                    >
                      <ExternalLink size={18} />
                    </a>
                  </div>
                </div>
              </div>
            ))}
          </div>
        )}
      </main>

      {/* Footer */}
      <footer className={`mt-20 py-12 border-t ${isDarkMode ? 'border-slate-800 text-slate-500' : 'border-slate-200 text-slate-400'}`}>
        <div className="container mx-auto px-6 text-center">
          <p>© {new Date().getFullYear()} Vibe Games Studio. Powered by Gemini.</p>
        </div>
      </footer>

      {/* Add Game Modal */}
      {isModalOpen && (
        <div className="fixed inset-0 z-50 flex items-center justify-center p-4">
          <div 
            className="absolute inset-0 bg-slate-950/60 backdrop-blur-sm"
            onClick={() => setIsModalOpen(false)}
          ></div>
          
          <div className={`relative w-full max-w-lg rounded-3xl shadow-2xl overflow-hidden animate-in fade-in zoom-in duration-200 ${isDarkMode ? 'bg-slate-900' : 'bg-white'}`}>
            <div className={`p-6 border-b flex justify-between items-center ${isDarkMode ? 'border-slate-800' : 'border-slate-200'}`}>
              <h3 className="text-xl font-bold">새 게임 프로젝트 추가</h3>
              <button 
                onClick={() => setIsModalOpen(false)}
                className="p-2 hover:bg-slate-100 dark:hover:bg-slate-800 rounded-full transition-colors"
              >
                <X size={20} />
              </button>
            </div>

            <form onSubmit={handleAddGame} className="p-6 space-y-5">
              <div className="space-y-2">
                <label className="text-sm font-bold flex items-center gap-2">
                  <Gamepad2 size={16} className="text-indigo-500" /> 게임 제목
                </label>
                <input 
                  type="text" 
                  name="title"
                  required
                  value={newGame.title}
                  onChange={handleInputChange}
                  placeholder="예: 스페이스 인베이더 2024"
                  className={`w-full px-4 py-3 rounded-xl border outline-none transition-all focus:ring-2 focus:ring-indigo-500/50 ${
                    isDarkMode ? 'bg-slate-800 border-slate-700 text-white' : 'bg-slate-50 border-slate-200'
                  }`}
                />
              </div>

              <div className="space-y-2">
                <label className="text-sm font-bold flex items-center gap-2">
                  <ExternalLink size={16} className="text-indigo-500" /> 게임 URL
                </label>
                <input 
                  type="url" 
                  name="url"
                  required
                  value={newGame.url}
                  onChange={handleInputChange}
                  placeholder="https://example.com/my-game"
                  className={`w-full px-4 py-3 rounded-xl border outline-none transition-all focus:ring-2 focus:ring-indigo-500/50 ${
                    isDarkMode ? 'bg-slate-800 border-slate-700 text-white' : 'bg-slate-50 border-slate-200'
                  }`}
                />
              </div>

              <div className="space-y-2">
                <label className="text-sm font-bold flex items-center gap-2">
                  <Info size={16} className="text-indigo-500" /> 설명 (선택사항)
                </label>
                <textarea 
                  name="description"
                  value={newGame.description}
                  onChange={handleInputChange}
                  rows="3"
                  placeholder="게임에 대한 간단한 설명을 적어주세요."
                  className={`w-full px-4 py-3 rounded-xl border outline-none transition-all focus:ring-2 focus:ring-indigo-500/50 resize-none ${
                    isDarkMode ? 'bg-slate-800 border-slate-700 text-white' : 'bg-slate-50 border-slate-200'
                  }`}
                ></textarea>
              </div>

              <div className="space-y-2">
                <label className="text-sm font-bold flex items-center gap-2">
                  <LayoutGrid size={16} className="text-indigo-500" /> 썸네일 이미지 URL (선택사항)
                </label>
                <input 
                  type="url" 
                  name="thumbnail"
                  value={newGame.thumbnail}
                  onChange={handleInputChange}
                  placeholder="https://example.com/image.png"
                  className={`w-full px-4 py-3 rounded-xl border outline-none transition-all focus:ring-2 focus:ring-indigo-500/50 ${
                    isDarkMode ? 'bg-slate-800 border-slate-700 text-white' : 'bg-slate-50 border-slate-200'
                  }`}
                />
              </div>

              <button 
                type="submit" 
                className="w-full bg-indigo-600 hover:bg-indigo-500 text-white font-bold py-4 rounded-xl transition-all shadow-lg shadow-indigo-500/30 mt-4"
              >
                컬렉션에 추가하기
              </button>
            </form>
          </div>
        </div>
      )}
    </div>
  );
};

export default App;
