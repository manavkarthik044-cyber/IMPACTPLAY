<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>IMPACTPLAY – Gamified IT Learning Hub</title>

<style>
:root{
  --bg:#07051A;
  --panel:#100D29;
  --panel2:#171238;
  --green:#00F5A0;
  --green2:#00D9FF;
  --cyan:#00E5FF;
  --purple:#9B5CFF;
  --pink:#FF4ECD;
  --text:#F5F3FF;
  --muted:#AAA6C8;
  --border:#30275C;
  --red:#FF5577;
  --yellow:#FFD166;
}

*{box-sizing:border-box}

body{
  margin:0;
  font-family:Inter,Arial,sans-serif;
  background:
    radial-gradient(circle at 10% 10%,rgba(155,92,255,.15),transparent 25%),
    radial-gradient(circle at 90% 20%,rgba(0,245,160,.08),transparent 25%),
    var(--bg);
  color:var(--text);
  min-height:100vh;
}

button,input{
  font:inherit;
}

button{
  cursor:pointer;
}

#app{
  min-height:100vh;
}

.nav{
  height:72px;
  padding:0 5%;
  display:flex;
  align-items:center;
  justify-content:space-between;
  border-bottom:1px solid var(--border);
  background:rgba(7,5,26,.9);
  backdrop-filter:blur(15px);
  position:sticky;
  top:0;
  z-index:20;
}

.logo{
  font-weight:900;
  font-size:21px;
  letter-spacing:1px;
}

.logo span{
  color:var(--green);
}

.nav-links{
  display:flex;
  gap:8px;
}

.nav-btn{
  border:0;
  background:transparent;
  color:var(--muted);
  padding:10px 14px;
  border-radius:10px;
}

.nav-btn:hover,
.nav-btn.active{
  color:var(--text);
  background:var(--panel2);
}

.logout{
  color:var(--red);
}

.container{
  width:min(1180px,92%);
  margin:auto;
  padding:35px 0 60px;
}

.hero{
  padding:25px 0;
}

h1{
  font-size:clamp(30px,5vw,52px);
  margin:0 0 10px;
  line-height:1.05;
}

h2{
  margin:0 0 8px;
}

h3{
  margin:0 0 7px;
}

p{
  color:var(--muted);
  line-height:1.6;
}

.gradient{
  background:linear-gradient(90deg,var(--green),var(--cyan),var(--purple),var(--pink));
  -webkit-background-clip:text;
  color:transparent;
}

.card{
  background:linear-gradient(145deg,rgba(23,18,56,.96),rgba(16,13,41,.96));
  border:1px solid var(--border);
  border-radius:18px;
  padding:22px;
  box-shadow:0 15px 50px rgba(0,0,0,.18);
}

.grid{
  display:grid;
  gap:18px;
}

.stats{
  grid-template-columns:repeat(4,1fr);
}

.categories{
  grid-template-columns:repeat(4,1fr);
}

.modes{
  grid-template-columns:repeat(5,1fr);
}

.stat-number{
  font-size:28px;
  font-weight:900;
  margin-top:5px;
}

.muted{
  color:var(--muted);
}

.small{
  font-size:13px;
}

.btn{
  border:1px solid var(--border);
  color:var(--text);
  background:var(--panel2);
  border-radius:11px;
  padding:11px 17px;
  transition:.2s;
}

.btn:hover{
  transform:translateY(-1px);
  border-color:var(--purple);
}

.btn.primary{
  border:0;
  color:#06120f;
  font-weight:800;
  background:linear-gradient(90deg,var(--green),var(--cyan));
}

.btn.danger{
  color:white;
  border-color:rgba(255,85,119,.4);
  background:rgba(255,85,119,.1);
}

.btn.warning{
  color:#17100a;
  border:0;
  background:var(--yellow);
}

.full{
  width:100%;
}

.progress{
  height:10px;
  background:#08061b;
  border-radius:100px;
  overflow:hidden;
}

.progress-fill{
  height:100%;
  background:linear-gradient(90deg,var(--green),var(--cyan),var(--purple));
  transition:.4s;
}

.category-card{
  min-height:200px;
  display:flex;
  flex-direction:column;
  justify-content:space-between;
  cursor:pointer;
  transition:.2s;
}

.category-card:hover{
  transform:translateY(-4px);
  border-color:var(--green);
}

.category-icon{
  font-size:42px;
  margin-bottom:15px;
}

.badge{
  display:inline-flex;
  align-items:center;
  padding:7px 10px;
  border-radius:30px;
  background:rgba(155,92,255,.12);
  border:1px solid rgba(155,92,255,.35);
  color:#d9c7ff;
  font-size:12px;
  margin:4px;
}

.auth-wrap{
  min-height:100vh;
  display:flex;
  align-items:center;
  justify-content:center;
  padding:20px;
}

.auth{
  width:min(440px,100%);
}

.auth-logo{
  text-align:center;
  margin-bottom:25px;
}

.auth-logo .logo{
  font-size:30px;
}

.tabs{
  display:grid;
  grid-template-columns:1fr 1fr;
  background:#09071c;
  padding:5px;
  border-radius:12px;
  margin-bottom:20px;
}

.tab{
  border:0;
  padding:11px;
  background:transparent;
  color:var(--muted);
  border-radius:9px;
}

.tab.active{
  background:var(--panel2);
  color:white;
}

.field{
  margin-bottom:15px;
}

.field label{
  display:block;
  margin-bottom:7px;
  color:#d8d3ef;
  font-size:14px;
}

.field input{
  width:100%;
  padding:13px;
  border-radius:10px;
  border:1px solid var(--border);
  outline:none;
  background:#09071d;
  color:white;
}

.field input:focus{
  border-color:var(--green);
}

.error{
  color:var(--red);
  font-size:14px;
  margin-bottom:12px;
}

.back{
  margin-bottom:20px;
}

.mode-card{
  min-height:150px;
  cursor:pointer;
  position:relative;
  overflow:hidden;
  transition:.2s;
}

.mode-card:hover{
  transform:translateY(-3px);
  border-color:var(--green);
}

.mode-card.completed{
  border-color:rgba(0,245,160,.5);
}

.mode-number{
  position:absolute;
  right:16px;
  top:14px;
  color:#544b78;
  font-size:30px;
  font-weight:900;
}

.game{
  max-width:850px;
  margin:auto;
}

.game-top{
  display:flex;
  justify-content:space-between;
  align-items:center;
  gap:15px;
  margin-bottom:18px;
}

.question{
  font-size:25px;
  line-height:1.35;
  margin:18px 0;
}

.answers{
  display:grid;
  gap:12px;
}

.answer{
  text-align:left;
  width:100%;
  padding:15px;
  border-radius:12px;
  border:1px solid var(--border);
  background:#0c0922;
  color:white;
  transition:.15s;
}

.answer:hover{
  border-color:var(--cyan);
}

.answer.correct{
  border-color:var(--green);
  background:rgba(0,245,160,.12);
}

.answer.wrong{
  border-color:var(--red);
  background:rgba(255,85,119,.12);
}

.answer.disabled{
  opacity:.35;
}

.game-actions{
  display:flex;
  gap:10px;
  flex-wrap:wrap;
  margin-top:20px;
}

.match-grid{
  display:grid;
  grid-template-columns:1fr 1fr;
  gap:12px;
}

.match-item{
  min-height:90px;
  padding:15px;
  border-radius:12px;
  border:1px solid var(--border);
  background:#0c0922;
  color:white;
  text-align:left;
}

.match-item.selected{
  border-color:var(--cyan);
  box-shadow:0 0 15px rgba(0,229,255,.15);
}

.match-item.matched{
  border-color:var(--green);
  opacity:.55;
}

.scramble-word{
  font-size:34px;
  font-weight:900;
  letter-spacing:5px;
  text-align:center;
  padding:25px;
  color:var(--green);
}

.sequence{
  display:grid;
  gap:10px;
}

.sequence-item{
  padding:17px;
  border:1px solid var(--border);
  background:#0c0922;
  border-radius:12px;
  text-align:left;
  color:white;
}

.sequence-item:hover{
  border-color:var(--purple);
}

.sequence-item.selected{
  border-color:var(--green);
  opacity:.6;
}

.timer{
  color:var(--yellow);
  font-size:24px;
  font-weight:900;
}

.result{
  text-align:center;
  padding:35px;
}

.result-icon{
  font-size:65px;
}

.leader-row{
  display:grid;
  grid-template-columns:55px 1fr 100px;
  gap:12px;
  align-items:center;
  padding:15px;
  border-bottom:1px solid var(--border);
}

.rank{
  font-size:22px;
  font-weight:900;
}

.profile-head{
  display:flex;
  gap:20px;
  align-items:center;
}

.avatar{
  width:80px;
  height:80px;
  border-radius:50%;
  display:flex;
  align-items:center;
  justify-content:center;
  font-size:30px;
  font-weight:900;
  background:linear-gradient(135deg,var(--purple),var(--green));
  color:#08051b;
}

.empty{
  text-align:center;
  padding:40px 20px;
  color:var(--muted);
}

@media(max-width:900px){
  .stats{grid-template-columns:repeat(2,1fr)}
  .categories{grid-template-columns:repeat(2,1fr)}
  .modes{grid-template-columns:repeat(2,1fr)}
}

@media(max-width:600px){
  .nav{
    height:auto;
    padding:12px 4%;
    flex-wrap:wrap;
    gap:10px;
  }

  .nav-links{
    width:100%;
    overflow:auto;
  }

  .nav-btn{
    white-space:nowrap;
  }

  .container{
    width:94%;
    padding-top:22px;
  }

  .stats,
  .categories,
  .modes,
  .match-grid{
    grid-template-columns:1fr;
  }

  .question{
    font-size:21px;
  }

  .card{
    padding:17px;
  }
}

@media(max-width:400px){
  .stats{
    grid-template-columns:1fr;
  }
}
</style>
</head>

<body>
<div id="app"></div>

<script>
/* =========================================================
   IMPACTPLAY - PLAIN HTML / CSS / JAVASCRIPT
   No React / npm / Vite required
========================================================= */

const CATEGORIES = {
  Networking:{
    icon:"🌐",
    color:"#00E5FF",
    description:"Learn networks, protocols and connectivity."
  },
  Cybersecurity:{
    icon:"🛡️",
    color:"#FF5577",
    description:"Build your cybersecurity knowledge."
  },
  Programming:{
    icon:"💻",
    color:"#9B5CFF",
    description:"Practice programming and development concepts."
  },
  "IT Support":{
    icon:"🔧",
    color:"#00F5A0",
    description:"Master troubleshooting and IT support."
  }
};

const QUESTIONS = {
Networking:[
 {q:"What does IP stand for?",a:["Internet Protocol","Internal Program","Internet Process","Interface Protocol"],c:0},
 {q:"Which device forwards packets between networks?",a:["Switch","Router","Hub","Repeater"],c:1},
 {q:"Which protocol is commonly used for secure web browsing?",a:["HTTP","FTP","HTTPS","SMTP"],c:2},
 {q:"What is the default port for HTTP?",a:["21","25","80","443"],c:2},
 {q:"Which device connects devices within a LAN?",a:["Switch","Router","Modem","Firewall"],c:0},
 {q:"What does DNS translate?",a:["MAC to RAM","Domain names to IP addresses","Files to folders","HTTP to FTP"],c:1},
 {q:"Which protocol is used to send email?",a:["SMTP","DNS","SSH","DHCP"],c:0},
 {q:"What does LAN mean?",a:["Large Area Network","Local Area Network","Linked Access Network","Local Access Node"],c:1},
 {q:"Which address identifies a network interface?",a:["MAC address","URL","Port","Domain"],c:0},
 {q:"Which protocol automatically assigns IP addresses?",a:["FTP","DHCP","SSH","TCP"],c:1}
],

Cybersecurity:[
 {q:"What is phishing?",a:["A backup method","A social engineering attack","A firewall","An encryption method"],c:1},
 {q:"What does malware mean?",a:["Malicious software","Managed software","Manual hardware","Main network"],c:0},
 {q:"Which is a strong password?",a:["12345678","password","K!9v#2Lm@7","qwerty"],c:2},
 {q:"What does MFA stand for?",a:["Multi-Factor Authentication","Main File Access","Managed Firewall Access","Multi File Authorization"],c:0},
 {q:"What is encryption used for?",a:["Deleting files","Protecting data","Increasing RAM","Creating networks"],c:1},
 {q:"What is a firewall?",a:["A security barrier","A programming language","A storage device","An email protocol"],c:0},
 {q:"What does antivirus software detect?",a:["Viruses and malware","IP addresses","Printers","Passwords only"],c:0},
 {q:"What is ransomware?",a:["A game","Malware that demands payment","A firewall","A backup"],c:1},
 {q:"Which principle means giving only necessary access?",a:["Least privilege","Open access","Maximum privilege","Full control"],c:0},
 {q:"Why are software updates important?",a:["They improve security","They remove the keyboard","They reduce storage to zero","They disable networks"],c:0}
],

Programming:[
 {q:"Which symbol starts a single-line comment in JavaScript?",a:["//","<!--","##","**"],c:0},
 {q:"Which keyword declares a constant in JavaScript?",a:["let","var","const","fixed"],c:2},
 {q:"What is a loop used for?",a:["Repeating instructions","Deleting code","Creating hardware","Changing monitors"],c:0},
 {q:"Which is a programming language?",a:["Python","HTML","Wi-Fi","USB"],c:0},
 {q:"What does IDE stand for?",a:["Integrated Development Environment","Internet Data Engine","Internal Design Editor","Integrated Device Element"],c:0},
 {q:"Which data type represents true or false?",a:["String","Boolean","Integer","Array"],c:1},
 {q:"What does a function contain?",a:["Reusable instructions","Only images","Hardware","Internet cables"],c:0},
 {q:"Which operator checks equality in JavaScript?",a:["=","===",":=","=>"],c:1},
 {q:"What is an array?",a:["A collection of values","A network","A browser","A compiler"],c:0},
 {q:"What does debugging mean?",a:["Finding and fixing errors","Writing emails","Installing RAM","Deleting programs"],c:0}
],

"IT Support":[
 {q:"What should you try first when a computer freezes?",a:["Restart immediately","Check what is unresponsive","Delete Windows","Replace the CPU"],c:1},
 {q:"What does RAM provide?",a:["Temporary working memory","Permanent storage","Internet service","Power"],c:0},
 {q:"Which device prints documents?",a:["Printer","Router","Switch","RAM"],c:0},
 {q:"What is an operating system?",a:["Software managing computer resources","A cable","A browser tab","A keyboard"],c:0},
 {q:"Which tool can test network connectivity?",a:["ping","paint","notepad","calculator"],c:0},
 {q:"What does USB stand for?",a:["Universal Serial Bus","United System Board","User Storage Block","Universal Software Base"],c:0},
 {q:"What is troubleshooting?",a:["Finding the cause of a problem","Installing games","Creating passwords","Designing websites"],c:0},
 {q:"Which component stores files permanently?",a:["RAM","SSD/HDD","CPU","Cache"],c:1},
 {q:"What is a driver?",a:["Software allowing hardware to communicate","A cable","A password","A browser"],c:0},
 {q:"What is a backup?",a:["A copy of data","A virus","A processor","A network port"],c:0}
]
};

const MATCHES = {
Networking:[
 ["Router","Forwards packets between networks"],
 ["DNS","Resolves domain names"],
 ["DHCP","Assigns IP addresses"],
 ["HTTP","Web communication protocol"],
 ["LAN","Local Area Network"]
],
Cybersecurity:[
 ["Phishing","Fraudulent attempt to steal information"],
 ["Firewall","Controls network traffic"],
 ["Encryption","Protects data using encoded information"],
 ["Ransomware","Malware demanding payment"],
 ["MFA","Uses multiple authentication factors"]
],
Programming:[
 ["Variable","Stores a value"],
 ["Loop","Repeats instructions"],
 ["Function","Reusable block of code"],
 ["Array","Collection of values"],
 ["Boolean","True or false value"]
],
"IT Support":[
 ["RAM","Temporary computer memory"],
 ["Driver","Connects hardware and software"],
 ["Backup","Copy of important data"],
 ["Troubleshooting","Finding and fixing problems"],
 ["Operating System","Manages computer resources"]
]
};

const SCRAMBLES = {
Networking:[
 ["ROUTER","A device that forwards packets"],
 ["PACKET","A unit of network data"],
 ["SERVER","Computer providing services"],
 ["DOMAIN","Human-readable website address"],
 ["SWITCH","Connects devices on a LAN"]
],
Cybersecurity:[
 ["PHISHING","Fraudulent attempt to steal information"],
 ["FIREWALL","Security barrier controlling traffic"],
 ["MALWARE","Malicious software"],
 ["PASSWORD","Secret authentication information"],
 ["ENCRYPTION","Converts information into protected form"]
],
Programming:[
 ["VARIABLE","Named storage for a value"],
 ["FUNCTION","Reusable block of instructions"],
 ["ARRAY","Collection of values"],
 ["LOOP","Repeats instructions"],
 ["DEBUG","Find and fix code errors"]
],
"IT Support":[
 ["PRINTER","Produces physical documents"],
 ["KEYBOARD","Input device for typing"],
 ["MONITOR","Displays computer output"],
 ["DRIVER","Software for hardware communication"],
 ["BACKUP","Copy of data"]
]
};

const SEQUENCES = {
Networking:[
 ["Connect the cable","Configure the network device","Assign an IP address","Test connectivity"],
 ["Open browser","Enter website address","DNS resolves domain","Server responds"],
 ["Create network","Connect devices","Configure addresses","Test communication"]
],
Cybersecurity:[
 ["Identify threat","Assess risk","Apply protection","Monitor system"],
 ["Receive suspicious email","Check sender","Avoid suspicious link","Report email"],
 ["Create password","Make it long","Add different characters","Enable MFA"]
],
Programming:[
 ["Understand problem","Plan solution","Write code","Test and debug"],
 ["Define variable","Assign value","Use variable","Display result"],
 ["Write function","Add parameters","Add instructions","Call function"]
],
"IT Support":[
 ["Identify issue","Collect information","Test possible cause","Apply solution"],
 ["Check power","Check cables","Check settings","Test device"],
 ["Receive ticket","Investigate issue","Resolve problem","Document solution"]
]
};

const MOCK_LEADERS = [
 {username:"Alex",xp:1480},
 {username:"Priya",xp:1260},
 {username:"Rahul",xp:1100},
 {username:"Sam",xp:980},
 {username:"Neha",xp:860}
];

const BADGES = {
quiz_rookie:["🧠","Quiz Rookie"],
perfectionist:["🏆","Perfectionist"],
matchmaker:["🔗","Matchmaker"],
unscrambler:["🔤","Unscrambler"],
sequencer:["📋","Sequencer"],
speed_demon:["⚡","Speed Demon"],
networking:["🌐","Networking Master"],
cybersecurity:["🛡️","Cybersecurity Master"],
programming:["💻","Programming Master"],
support:["🔧","IT Support Master"]
};

let users = loadUsers();
let current = localStorage.getItem("impactplay_current") || null;

let state = {
  screen:"dashboard",
  authMode:"login",
  category:null,
  mode:null,
  game:null
};

function loadUsers(){
  try{
    return JSON.parse(localStorage.getItem("impactplay_users") || "{}");
  }catch(e){
    return {};
  }
}

function saveUsers(){
  localStorage.setItem("impactplay_users",JSON.stringify(users));
}

function getUser(){
  return current ? users[current] : null;
}

function esc(value){
  return String(value ?? "")
    .replace(/&/g,"&amp;")
    .replace(/</g,"&lt;")
    .replace(/>/g,"&gt;")
    .replace(/"/g,"&quot;")
    .replace(/'/g,"&#039;");
}

function level(xp){
  return Math.floor(xp / 250) + 1;
}

function completedCount(user){
  return Object.values(user.completed || {}).filter(Boolean).length;
}

function addXP(amount){
  const user=getUser();
  if(!user)return;

  user.xp=(user.xp||0)+amount;
  saveUsers();
}

function awardBadge(id){
  const user=getUser();
  if(!user)return;

  user.badges=user.badges||[];

  if(!user.badges.includes(id)){
    user.badges.push(id);
    saveUsers();
  }
}

function completeMode(category,mode){
  const user=getUser();
  if(!user)return;

  user.completed=user.completed||{};
  user.completed[category+"_"+mode]=true;

  const ids={
    Networking:"networking",
    Cybersecurity:"cybersecurity",
    Programming:"programming",
    "IT Support":"support"
  };

  awardBadge(ids[category]);
  saveUsers();
}

function modeDone(category,mode){
  const user=getUser();
  return !!user?.completed?.[category+"_"+mode];
}

function shuffle(arr){
  return [...arr].sort(()=>Math.random()-.5);
}

function render(){
  if(!current || !users[current]){
    renderAuth();
    return;
  }

  renderApp();
}

function renderAuth(){
  document.getElementById("app").innerHTML=`
    <div class="auth-wrap">
      <div class="auth">
        <div class="auth-logo">
          <div class="logo">IMPACT<span>PLAY</span></div>
          <p>Gamified IT Learning Hub</p>
        </div>

        <div class="card">
          <div class="tabs">
            <button class="tab ${state.authMode==="login"?"active":""}"
              onclick="setAuth('login')">Login</button>
            <button class="tab ${state.authMode==="register"?"active":""}"
              onclick="setAuth('register')">Create Account</button>
          </div>

          <form onsubmit="authSubmit(event)">
            <div class="field">
              <label>Username</label>
              <input id="authUsername" required minlength="3" autocomplete="username">
            </div>

            <div class="field">
              <label>Password</label>
              <input id="authPassword" type="password" required minlength="4"
                autocomplete="${state.authMode==="login"?"current-password":"new-password"}">
            </div>

            <div id="authError"></div>

            <button class="btn primary full" type="submit">
              ${state.authMode==="login"?"Login":"Create Account"}
            </button>
          </form>

          <p class="small" style="text-align:center;margin-bottom:0">
            Your progress is saved in this browser.
          </p>
        </div>
      </div>
    </div>
  `;
}

function setAuth(mode){
  state.authMode=mode;
  render();
}

function authSubmit(e){
  e.preventDefault();

  const username=document.getElementById("authUsername").value.trim();
  const password=document.getElementById("authPassword").value;

  const error=document.getElementById("authError");

  if(state.authMode==="register"){
    if(users[username]){
      error.innerHTML=`<div class="error">Username already exists.</div>`;
      return;
    }

    users[username]={
      username,
      password,
      xp:0,
      badges:[],
      completed:{}
    };

    saveUsers();

    current=username;
    localStorage.setItem("impactplay_current",current);

    state.screen="dashboard";
    render();
    return;
  }

  if(!users[username] || users[username].password!==password){
    error.innerHTML=`<div class="error">Incorrect username or password.</div>`;
    return;
  }

  current=username;
  localStorage.setItem("impactplay_current",current);

  state.screen="dashboard";
  render();
}

function logout(){
  current=null;
  localStorage.removeItem("impactplay_current");
  state.screen="dashboard";
  state.category=null;
  state.mode=null;
  state.game=null;
  render();
}

function renderApp(){
  let content="";

  if(state.screen==="dashboard") content=dashboardHTML();
  else if(state.screen==="leaderboard") content=leaderboardHTML();
  else if(state.screen==="profile") content=profileHTML();
  else if(state.screen==="category") content=categoryHTML();
  else if(state.screen==="game") content=gameHTML();

  document.getElementById("app").innerHTML=`
    ${navbarHTML()}
    <main class="container">${content}</main>
  `;
}

function navbarHTML(){
  return`
    <nav class="nav">
      <div class="logo">IMPACT<span>PLAY</span></div>

      <div class="nav-links">
        <button class="nav-btn ${state.screen==="dashboard"?"active":""}"
          onclick="goDashboard()">🏠 Dashboard</button>

        <button class="nav-btn ${state.screen==="leaderboard"?"active":""}"
          onclick="goLeaderboard()">🏆 Leaderboard</button>

        <button class="nav-btn ${state.screen==="profile"?"active":""}"
          onclick="goProfile()">👤 Profile</button>

        <button class="nav-btn logout" onclick="logout()">Logout</button>
      </div>
    </nav>
  `;
}

function goDashboard(){
  state.screen="dashboard";
  state.category=null;
  state.mode=null;
  state.game=null;
  render();
}

function goLeaderboard(){
  state.screen="leaderboard";
  render();
}

function goProfile(){
  state.screen="profile";
  render();
}

function dashboardHTML(){
  const u=getUser();

  return`
    <section class="hero">
      <p class="small">WELCOME BACK</p>
      <h1>Level up your <span class="gradient">IT skills.</span></h1>
      <p>Learn through games, earn XP and unlock badges.</p>
    </section>

    <div class="grid stats">
      <div class="card">
        <div class="muted small">TOTAL XP</div>
        <div class="stat-number">${u.xp||0}</div>
      </div>

      <div class="card">
        <div class="muted small">LEVEL</div>
        <div class="stat-number">${level(u.xp||0)}</div>
      </div>

      <div class="card">
        <div class="muted small">BADGES</div>
        <div class="stat-number">${(u.badges||[]).length}</div>
      </div>

      <div class="card">
        <div class="muted small">COMPLETED</div>
        <div class="stat-number">${completedCount(u)}</div>
      </div>
    </div>

    <div style="height:35px"></div>

    <div style="display:flex;justify-content:space-between;align-items:end;margin-bottom:15px">
      <div>
        <p class="small" style="margin:0">CHOOSE A CATEGORY</p>
        <h2>Start Learning</h2>
      </div>
    </div>

    <div class="grid categories">
      ${Object.keys(CATEGORIES).map(category=>{
        const c=CATEGORIES[category];

        return`
          <div class="card category-card" onclick="openCategory('${esc(category)}')">
            <div>
              <div class="category-icon">${c.icon}</div>
              <h3>${category}</h3>
              <p class="small">${c.description}</p>
            </div>
            <button class="btn primary">Play →</button>
          </div>
        `;
      }).join("")}
    </div>
  `;
}

function openCategory(category){
  state.category=category;
  state.screen="category";
  state.mode=null;
  state.game=null;
  render();
}

function categoryHTML(){
  const category=state.category;
  const u=getUser();

  const xp=u.xp||0;
  const levelXP=xp%250;
  const progress=(levelXP/250)*100;

  const modes=[
    ["quiz","🧠","Quiz Run","Answer IT questions"],
    ["match","🔗","Match Grid","Connect terms and definitions"],
    ["scramble","🔤","Word Scramble","Unscramble IT words"],
    ["sequence","📋","Sequence Sort","Put steps in order"],
    ["timed","⚡","Timed Sprint","Answer before time runs out"]
  ];

  return`
    <button class="btn back" onclick="goDashboard()">← Back to Dashboard</button>

    <div class="card" style="margin-bottom:20px">
      <div style="display:flex;justify-content:space-between;gap:15px">
        <div>
          <p class="small" style="margin:0">${CATEGORIES[category].icon} CATEGORY</p>
          <h1>${category}</h1>
          <p>${CATEGORIES[category].description}</p>
        </div>

        <div style="text-align:right">
          <div class="stat-number">${xp} XP</div>
          <div class="small muted">Level ${level(u.xp||0)}</div>
        </div>
      </div>

      <div class="progress">
        <div class="progress-fill" style="width:${progress}%"></div>
      </div>
      <p class="small">Progress to next level: ${levelXP}/250 XP</p>
    </div>

    <h2>Game Modes</h2>
    <p>Choose a game and start earning XP.</p>

    <div class="grid modes">
      ${modes.map((m,i)=>{
        const done=modeDone(category,m[0]);

        return`
          <div class="card mode-card ${done?"completed":""}"
               onclick="startGame('${m[0]}')">
            <div class="mode-number">${i+1}</div>
            <div style="font-size:35px">${m[1]}</div>
            <h3>${m[2]}</h3>
            <p class="small">${m[3]}</p>
            ${done?'<span class="badge">✓ Completed</span>':''}
          </div>
        `;
      }).join("")}
    </div>
  `;
}

function startGame(mode){
  state.mode=mode;
  state.screen="game";

  if(mode==="quiz") initQuiz();
  if(mode==="match") initMatch();
  if(mode==="scramble") initScramble();
  if(mode==="sequence") initSequence();
  if(mode==="timed") initTimed();

  render();
}

/* =========================================================
   QUIZ
========================================================= */

function initQuiz(){
  const questions=shuffle(QUESTIONS[state.category]);

  state.game={
    type:"quiz",
    questions,
    index:0,
    score:0,
    streak:0,
    hintUsed:false,
    selected:null,
    finished:false
  };
}

function quizHTML(){
  const g=state.game;

  if(g.finished){
    return resultHTML(
      "🧠",
      "Quiz Complete!",
      `You scored ${g.score}/${g.questions.length}`,
      g.xp
    );
  }

  const q=g.questions[g.index];

  let answers=q.a.map((answer,i)=>{
    let cls="";

    if(g.selected!==null){
      if(i===q.c) cls="correct";
      else if(i===g.selected) cls="wrong";
    }

    if(g.hintUsed && i!==q.c && i!==g.hintWrong) cls+=" disabled";

    return`
      <button class="answer ${cls}"
        ${g.selected!==null||(
          g.hintUsed&&i===g.hintWrong
        )?"disabled":""}
        onclick="answerQuiz(${i})">
        <strong>${String.fromCharCode(65+i)}.</strong> ${esc(answer)}
      </button>
    `;
  }).join("");

  return`
    <div class="game">
      <div class="game-top">
        <div>
          <span class="badge">${state.category}</span>
          <span class="muted">Question ${g.index+1}/${g.questions.length}</span>
        </div>
        <div>🔥 Streak: <strong>${g.streak}</strong></div>
      </div>

      <div class="progress">
        <div class="progress-fill"
          style="width:${((g.index+1)/g.questions.length)*100}%"></div>
      </div>

      <div class="card" style="margin-top:18px">
        <div class="question">${esc(q.q)}</div>

        <div class="answers">${answers}</div>

        <div class="game-actions">
          ${!g.hintUsed&&g.selected===null?
            `<button class="btn warning" onclick="quizHint()">💡 Hint</button>`:""}

          ${g.selected!==null?
            `<button class="btn primary" onclick="nextQuiz()">
              ${g.index===g.questions.length-1?"Finish":"Next →"}
            </button>`:""}
        </div>
      </div>
    </div>
  `;
}

function answerQuiz(index){
  const g=state.game;
  if(g.selected!==null)return;

  g.selected=index;

  if(index===g.questions[g.index].c){
    g.score++;
    g.streak++;
  }else{
    g.streak=0;
  }

  render();
}

function quizHint(){
  const g=state.game;
  const q=g.questions[g.index];

  const wrong=q.a.map((_,i)=>i).filter(i=>i!==q.c);

  g.hintWrong=wrong[Math.floor(Math.random()*wrong.length)];
  g.hintUsed=true;

  render();
}

function nextQuiz(){
  const g=state.game;

  if(g.index===g.questions.length-1){
    g.xp=g.score*10+g.streak*2;

    addXP(g.xp);
    awardBadge("quiz_rookie");

    if(g.score===g.questions.length){
      awardBadge("perfectionist");
    }

    completeMode(state.category,"quiz");
    g.finished=true;
    saveUsers();
    render();
    return;
  }

  g.index++;
  g.selected=null;
  g.hintUsed=false;
  g.hintWrong=null;

  render();
}

/* =========================================================
   MATCH
========================================================= */

function initMatch(){
  const pairs=MATCHES[state.category];

  state.game={
    type:"match",
    terms:shuffle(pairs.map((p,i)=>({id:i,text:p[0]}))),
    defs:shuffle(pairs.map((p,i)=>({id:i,text:p[1]}))),
    selectedTerm:null,
    matched:[],
    mistakes:0,
    hint:null,
    finished:false
  };
}

function matchHTML(){
  const g=state.game;

  if(g.finished){
    return resultHTML(
      "🔗",
      "Match Complete!",
      `${g.matched.length}/5 matched • ${g.mistakes} mistakes`,
      g.xp
    );
  }

  return`
    <div class="game">
      <div class="game-top">
        <div>
          <span class="badge">${state.category}</span>
          <span class="muted">Match Grid</span>
        </div>
        <div>Mistakes: ${g.mistakes}</div>
      </div>

      <div class="card">
        <p>Select a term, then select its matching definition.</p>

        <div class="match-grid">
          <div>
            <p class="small">TERMS</p>
            ${g.terms.map(x=>{
              const matched=g.matched.includes(x.id);

              return`
                <button class="match-item
                  ${g.selectedTerm===x.id?"selected":""}
                  ${matched?"matched":""}"
                  ${matched?"disabled":""}
                  onclick="selectTerm(${x.id})">
                  ${esc(x.text)}
                </button>
              `;
            }).join("")}
          </div>

          <div>
            <p class="small">DEFINITIONS</p>
            ${g.defs.map(x=>{
              const matched=g.matched.includes(x.id);

              return`
                <button class="match-item
                  ${g.hint===x.id?"selected":""}
                  ${matched?"matched":""}"
                  ${matched?"disabled":""}
                  onclick="selectDefinition(${x.id})">
                  ${esc(x.text)}
                </button>
              `;
            }).join("")}
          </div>
        </div>

        <div class="game-actions">
          <button class="btn warning" onclick="matchHint()">💡 Hint</button>
        </div>
      </div>
    </div>
  `;
}

function selectTerm(id){
  if(state.game.matched.includes(id))return;

  state.game.selectedTerm=id;
  state.game.hint=null;

  render();
}

function selectDefinition(id){
  const g=state.game;

  if(g.selectedTerm===null)return;
  if(g.matched.includes(id))return;

  if(g.selectedTerm===id){
    g.matched.push(id);
    g.selectedTerm=null;

    if(g.matched.length===5){
      g.xp=40+(g.mistakes===0?20:0);

      addXP(g.xp);
      awardBadge("matchmaker");
      completeMode(state.category,"match");

      g.finished=true;
    }
  }else{
    g.mistakes++;
    g.selectedTerm=null;
  }

  render();
}

function matchHint(){
  const g=state.game;

  const available=MATCHES[state.category]
    .map((_,i)=>i)
    .filter(i=>!g.matched.includes(i));

  if(available.length){
    g.hint=available[Math.floor(Math.random()*available.length)];
  }

  render();
}

/* =========================================================
   SCRAMBLE
========================================================= */

function initScramble(){
  const words=shuffle(SCRAMBLES[state.category]);

  state.game={
    type:"scramble",
    words,
    index:0,
    score:0,
    input:"",
    hint:"",
    finished:false
  };
}

function scrambleHTML(){
  const g=state.game;

  if(g.finished){
    return resultHTML(
      "🔤",
      "Scramble Complete!",
      `You solved ${g.score}/${g.words.length} words`,
      g.xp
    );
  }

  const word=g.words[g.index];
  const scrambled=shuffle(word[0].split("")).join("");

  return`
    <div class="game">
      <div class="game-top">
        <div>
          <span class="badge">${state.category}</span>
          <span class="muted">Word ${g.index+1}/${g.words.length}</span>
        </div>
        <div>Score: ${g.score}</div>
      </div>

      <div class="card">
        <p class="small" style="text-align:center">${esc(word[1])}</p>

        <div class="scramble-word">${scrambled}</div>

        <div class="field">
          <input
            id="scrambleInput"
            placeholder="Type the correct word..."
            value="${esc(g.input)}"
            oninput="state.game.input=this.value.toUpperCase()"
            onkeydown="if(event.key==='Enter')submitScramble()"
          >
        </div>

        ${g.hint?
          `<p style="text-align:center;color:var(--yellow)">
            💡 ${esc(g.hint)}
          </p>`:""}

        <div class="game-actions">
          <button class="btn warning" onclick="scrambleHint()">💡 Hint</button>
          <button class="btn primary" onclick="submitScramble()">Submit</button>
        </div>
      </div>
    </div>
  `;
}

function scrambleHint(){
  const g=state.game;
  const word=g.words[g.index][0];

  const current=g.input||"";
  let next=word.split("").find((letter,i)=>current[i]!==letter);

  g.hint=next ? `The next correct letter is "${next}"` : "Keep going!";
  render();
}

function submitScramble(){
  const g=state.game;
  const word=g.words[g.index][0];

  if((g.input||"").trim().toUpperCase()===word){
    g.score++;
  }

  if(g.index===g.words.length-1){
    g.xp=g.score*12;

    addXP(g.xp);
    awardBadge("unscrambler");
    completeMode(state.category,"scramble");

    g.finished=true;
  }else{
    g.index++;
    g.input="";
    g.hint="";
  }

  render();
}

/* =========================================================
   SEQUENCE
========================================================= */

function initSequence(){
  const items=shuffle(SEQUENCES[state.category]);

  state.game={
    type:"sequence",
    items,
    index:0,
    selected:[],
    finished:false
  };
}

function sequenceHTML(){
  const g=state.game;

  if(g.finished){
    return resultHTML(
      "📋",
      "Sequence Complete!",
      `${g.correctCount}/${g.items[g.index].length} steps correct`,
      g.xp
    );
  }

  const steps=g.items[g.index];

  return`
    <div class="game">
      <div class="game-top">
        <div>
          <span class="badge">${state.category}</span>
          <span class="muted">Sequence Sort</span>
        </div>
        <div>${g.selected.length}/${steps.length}</div>
      </div>

      <div class="card">
        <p>Click the steps in the correct order.</p>

        <div class="sequence">
          ${steps.map((step,i)=>{
            const selected=g.selected.indexOf(i);

            return`
              <button class="sequence-item ${selected>=0?"selected":""}"
                ${selected>=0?"disabled":""}
                onclick="selectSequence(${i})">
                ${selected>=0?
                  `<strong>${selected+1}.</strong> `:""}
                ${esc(step)}
              </button>
            `;
          }).join("")}
        </div>

        <div class="game-actions">
          <button class="btn warning" onclick="sequenceHint()">💡 Hint</button>
          <button class="btn" onclick="resetSequence()">Reset</button>
        </div>
      </div>
    </div>
  `;
}

function selectSequence(id){
  const g=state.game;
  const steps=g.items[g.index];

  g.selected.push(id);

  if(g.selected.length===steps.length){
    let correct=0;

    g.selected.forEach((value,i)=>{
      if(value===i)correct++;
    });

    g.correctCount=correct;
    g.xp=correct===steps.length?60:correct*10;

    addXP(g.xp);
    awardBadge("sequencer");
    completeMode(state.category,"sequence");

    g.finished=true;
  }

  render();
}

function resetSequence(){
  state.game.selected=[];
  render();
}

function sequenceHint(){
  const g=state.game;
  const steps=g.items[g.index];

  const next=steps.findIndex((_,i)=>!g.selected.includes(i));

  if(next>=0){
    alert(`Hint: choose "${steps[next]}" next.`);
  }
}

/* =========================================================
   TIMED SPRINT
========================================================= */

function initTimed(){
  state.game={
    type:"timed",
    questions:shuffle(QUESTIONS[state.category]),
    index:0,
    score:0,
    time:60,
    hintUsed:false,
    selected:null,
    finished:false,
    started:false,
    timer:null
  };

  startTimer();
}

function startTimer(){
  const g=state.game;

  if(g.timer)clearInterval(g.timer);

  g.timer=setInterval(()=>{
    if(state.mode!=="timed" || !state.game){
      clearInterval(g.timer);
      return;
    }

    g.time--;

    if(g.time<=0){
      finishTimed();
      return;
    }

    render();
  },1000);
}

function timedHTML(){
  const g=state.game;

  if(g.finished){
    return resultHTML(
      "⚡",
      "Sprint Complete!",
      `You answered ${g.score} questions correctly`,
      g.xp
    );
  }

  const q=g.questions[g.index % g.questions.length];

  return`
    <div class="game">
      <div class="game-top">
        <div>
          <span class="badge">${state.category}</span>
          <span class="muted">Timed Sprint</span>
        </div>

        <div class="timer">⏱ ${g.time}s</div>
      </div>

      <div class="card">
        <div class="question">${esc(q.q)}</div>

        <div class="answers">
          ${q.a.map((a,i)=>{
            let disabled="";

            if(g.selected!==null)disabled="disabled";

            if(g.hintUsed&&i===g.hintWrong)disabled="disabled";

            return`
              <button class="answer"
                ${disabled}
                onclick="answerTimed(${i})">
                ${String.fromCharCode(65+i)}. ${esc(a)}
              </button>
            `;
          }).join("")}
        </div>

        <div class="game-actions">
          <button class="btn warning" onclick="timedHint()">💡 Hint (-3 sec)</button>
        </div>

        <p class="small">
          Correct answers: <strong>${g.score}</strong>
        </p>
      </div>
    </div>
  `;
}

function answerTimed(index){
  const g=state.game;

  if(g.selected!==null)return;

  const q=g.questions[g.index % g.questions.length];

  g.selected=index;

  if(index===q.c){
    g.score++;
  }

  setTimeout(()=>{
    if(!g.finished){
      g.index++;
      g.selected=null;
      g.hintUsed=false;
      g.hintWrong=null;
      render();
    }
  },300);
}

function timedHint(){
  const g=state.game;
  const q=g.questions[g.index % g.questions.length];

  const wrong=q.a.map((_,i)=>i).filter(i=>i!==q.c);

  g.hintWrong=wrong[Math.floor(Math.random()*wrong.length)];
  g.hintUsed=true;
  g.time=Math.max(1,g.time-3);

  render();
}

function finishTimed(){
  const g=state.game;

  if(g.finished)return;

  clearInterval(g.timer);

  g.xp=g.score*15;

  addXP(g.xp);
  awardBadge("speed_demon");
  completeMode(state.category,"timed");

  g.finished=true;

  render();
}

/* =========================================================
   GAMES ROUTER
========================================================= */

function gameHTML(){
  if(!state.game)return "";

  let body="";

  if(state.mode==="quiz")body=quizHTML();
  if(state.mode==="match")body=matchHTML();
  if(state.mode==="scramble")body=scrambleHTML();
  if(state.mode==="sequence")body=sequenceHTML();
  if(state.mode==="timed")body=timedHTML();

  return`
    <button class="btn back" onclick="backToCategory()">← Back</button>
    ${body}
  `;
}

function backToCategory(){
  if(state.game?.timer)clearInterval(state.game.timer);

  state.screen="category";
  state.mode=null;
  state.game=null;

  render();
}

function resultHTML(icon,title,description,xp){
  return`
    <div class="game">
      <div class="card result">
        <div class="result-icon">${icon}</div>
        <h1>${title}</h1>
        <p>${description}</p>

        <div class="stat-number gradient">+${xp} XP</div>

        <div style="margin:20px 0">
          <span class="badge">🎉 Great job!</span>
        </div>

        <div class="game-actions" style="justify-content:center">
          <button class="btn primary"
            onclick="backToCategory()">Continue</button>

          <button class="btn"
            onclick="goDashboard()">Dashboard</button>
        </div>
      </div>
    </div>
  `;
}

/* =========================================================
   PROFILE
========================================================= */

function profileHTML(){
  const u=getUser();
  const xp=u.xp||0;
  const currentLevel=level(xp);
  const progress=((xp%250)/250)*100;

  return`
    <div style="max-width:850px;margin:auto">
      <div class="card">
        <div class="profile-head">
          <div class="avatar">
            ${esc(u.username.charAt(0).toUpperCase())}
          </div>

          <div>
            <p class="small" style="margin:0">PROFILE</p>
            <h1 style="font-size:34px">${esc(u.username)}</h1>
            <p style="margin:0">Level ${currentLevel} • ${xp} XP</p>
          </div>
        </div>

        <div style="margin-top:30px">
          <div style="display:flex;justify-content:space-between">
            <span>Level ${currentLevel}</span>
            <span class="muted">${xp%250}/250 XP</span>
          </div>

          <div class="progress" style="margin-top:8px">
            <div class="progress-fill" style="width:${progress}%"></div>
          </div>
        </div>
      </div>

      <div style="height:20px"></div>

      <div class="card">
        <h2>Badges</h2>
        <p>Achievements you have unlocked.</p>

        <div>
          ${(u.badges||[]).length
            ?u.badges.map(id=>{
              const b=BADGES[id];
              return `<span class="badge">${b[0]} ${b[1]}</span>`;
            }).join("")
            :`<div class="empty">No badges yet. Play a game to earn your first one!</div>`
          }
        </div>
      </div>
    </div>
  `;
}

/* =========================================================
   LEADERBOARD
========================================================= */

function leaderboardHTML(){
  const u=getUser();

  const leaders=[
    ...MOCK_LEADERS.filter(x=>x.username!==u.username),
    {username:u.username,xp:u.xp||0}
  ].sort((a,b)=>b.xp-a.xp);

  return`
    <div style="max-width:800px;margin:auto">
      <div class="hero">
        <p class="small">COMPETE</p>
        <h1>Leaderboard <span class="gradient">🏆</span></h1>
        <p>See how you rank against other learners.</p>
      </div>

      <div class="card">
        ${leaders.map((leader,i)=>{
          const me=leader.username===u.username;

          return`
            <div class="leader-row"
              style="${me?"background:rgba(0,245,160,.06)":""}">
              <div class="rank">
                ${i===0?"🥇":i===1?"🥈":i===2?"🥉":i+1}
              </div>

              <div>
                <strong>${esc(leader.username)}</strong>
                ${me?'<span class="badge">YOU</span>':""}
              </div>

              <div style="text-align:right">
                <strong>${leader.xp}</strong>
                <div class="small muted">XP</div>
              </div>
            </div>
          `;
        }).join("")}
      </div>
    </div>
  `;
}

/* =========================================================
   START
========================================================= */

render();
</script>
</body>
</html>
