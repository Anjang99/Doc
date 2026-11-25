<!DOCTYPE html>  
<html lang="id">  
<head>  
<meta charset="UTF-8">  
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">  
<title>Dokumentasi Pekerjaan - Offline</title>  
<meta name="apple-mobile-web-app-capable" content="yes">  
<meta name="theme-color" content="#0A1F3D">  
<style>  
*{box-sizing:border-box;font-family:-apple-system,Inter,system-ui,sans-serif}  
body{margin:0;background:#F1F5F9;color:#0A1F3D;padding-bottom:20px}  
header{background:#0A1F3D;color:#fff;padding:14px 16px;position:sticky;top:0;z-index:10;display:flex;align-items:center;gap:10px}  
header b{font-size:20px} header span{color:#C9A86A}  
header small{display:block;font-size:11px;color:#CBD5E1;font-weight:400}  
.wrap{max-width:720px;margin:auto;padding:12px}  
.card{background:#fff;border-radius:16px;padding:16px;margin-bottom:12px}  
h3{margin:0 0 12px;font-size:16px;border-left:4px solid #C9A86A;padding-left:8px}  
label{font-size:13px;font-weight:600;display:block;margin:12px 0 5px}  
input,select,textarea{width:100%;padding:12px;border:1.5px solid #E2E8F0;border-radius:10px;font-size:15px}  
.foto-box{border:2px dashed #CBD5E1;border-radius:12px;padding:16px;text-align:center;cursor:pointer;background:#F8FAFC}  
#preview{display:grid;grid-template-columns:repeat(3,1fr);gap:8px;margin-top:10px}  
#preview div{position:relative}  
#preview img{width:100%;height:90px;object-fit:cover;border-radius:10px}  
#preview button{position:absolute;top:4px;right:4px;background:#DC2626;color:#fff;border:none;width:24px;height:24px;border-radius:50%;font-weight:800}  
.btn{width:100%;padding:14px;border:none;border-radius:12px;background:#0A1F3D;color:#fff;font-weight:700;font-size:15px;cursor:pointer}  
.btn-green{background:#16A34A}.btn-gold{background:#C9A86A;color:#0A1F3D}.btn-red{background:#DC2626}  
.btn-small{padding:10px;font-size:13px;width:auto}  
.row{display:flex;gap:8px}.row>*{flex:1}  
.stat{display:flex;gap:8px}.stat div{flex:1;background:#fff;border-radius:14px;padding:12px;text-align:center}.stat b{font-size:20px;display:block}  
.grid{display:grid;grid-template-columns:1fr 1fr;gap:12px}  
.doc{background:#fff;border-radius:16px;overflow:hidden;border:1px solid #E2E8F0}  
.doc img{width:100%;height:150px;object-fit:cover;display:block}  
.doc-body{padding:12px}.doc-body b{font-size:14px;display:block}  
.doc-body small{color:#64748B;font-size:12px;display:block;margin:4px 0}  
.badge{display:inline-block;background:#FEF3C7;color:#92400E;font-size:11px;font-weight:700;padding:4px 8px;border-radius:99px}  
.ok{display:none;background:#DCFCE7;padding:12px;border-radius:10px;text-align:center;font-weight:700;color:#166534;margin-top:10px}  
.hidden{display:none}  
.modal{position:fixed;inset:0;background:rgba(0,0,0,.9);display:grid;place-items:center;padding:12px;z-index:50}  
.modal-box{width:100%;max-width:600px;background:#fff;border-radius:16px;overflow:hidden;max-height:92vh;overflow-y:auto}  
.modal-box img{width:100%}  
.modal-body{padding:16px}  
.chip{padding:8px 12px;border-radius:99px;border:1.5px solid #E2E8F0;background:#fff;font-weight:600;font-size:13px;cursor:pointer}  
.chip.on{background:#0A1F3D;color:#fff}  
.offline-bar{display:none;background:#FEF3C7;color:#92400E;text-align:center;padding:8px;font-size:13px;font-weight:700}  
.offline-bar.show{display:block}  
@media(max-width:500px){.grid{grid-template-columns:1fr}}  
</style>  
</head>  
<body>  
<header><div style="flex:1"><b>Dokumentasi <span>Pekerjaan</span></b><small>✅ 100% OFFLINE • Tanpa Internet</small></div><span id="statusDot">🟢</span></header>  
<div id="offlineBar" class="offline-bar">📴 Mode Offline - Foto tetap bisa dilihat & disimpan</div>  
<div class="wrap">  
<div class="stat"><div><b id="totalDok">0</b><small>Total Dokumentasi</small></div><div><b id="totalFoto">0</b><small>Total Foto</small></div><div><b id="hariIni">0</b><small>Hari Ini</small></div></div>  
<div class="card"><h3>📸 Tambah Dokumentasi (Offline)</h3>  
<label>Judul Pekerjaan *</label><input id="judul" placeholder="Contoh: Perbaikan Jalan - Surabaya">  
<div class="row"><div><label>Tanggal *</label><input type="date" id="tgl"></div><div><label>Kategori</label><select id="kategori"><option>Progres Pekerjaan</option><option>Before / Sebelum</option><option>After / Sesudah</option><option>Kerusakan</option><option>Material</option><option>Lainnya</option></select></div></div>  
<label>Lokasi Pekerjaan</label><input id="lokasi" placeholder="Jl. Raya Darmo, Surabaya">  
<label>Keterangan / Catatan</label><textarea id="ket" rows="3" placeholder="Tulis detail pekerjaan..."></textarea>  
<label>Foto Dokumentasi * (Bisa Banyak)</label>  
<div class="foto-box" onclick="el('inputFoto').click()"><b>📷 Klik Untuk Ambil / Pilih Foto</b><br><small>Bisa banyak foto, langsung tersimpan di HP</small><input type="file" id="inputFoto" accept="image/*" multiple hidden><div id="preview"></div></div>  
<button class="btn btn-green" onclick="simpan()" style="margin-top:14px">💾 Simpan - Bisa Offline</button><div class="ok" id="sukses">✅ Tersimpan Offline di HP Ini!</div></div>  
<div class="card"><h3>🔍 Cari & Filter</h3><label>Cari Judul / Lokasi</label><input id="cari" placeholder="Ketik untuk cari..." oninput="render()">  
<div style="display:flex;gap:6px;flex-wrap:wrap;margin-top:10px"><button class="chip on" onclick="setFilter('Semua',this)">Semua</button><button class="chip" onclick="setFilter('Progres Pekerjaan',this)">Progres</button><button class="chip" onclick="setFilter('Before / Sebelum',this)">Before</button><button class="chip" onclick="setFilter('After / Sesudah',this)">After</button><button class="chip" onclick="setFilter('Kerusakan',this)">Kerusakan</button></div>  
<div class="row" style="margin-top:12px"><button class="btn btn-gold" onclick="downloadExcel()">⬇️ Download Excel</button><button class="btn btn-red" onclick="hapusSemua()">🗑️ Hapus Semua</button></div></div>  
<div id="listDok"></div>  
<p style="text-align:center;color:#94A3B8;font-size:12px">Data tersimpan di HP ini. Bisa Mode Pesawat. Install: Safari > Share > Add to Home Screen</p>  
</div>  
<div id="modal" class="modal hidden" onclick="if(event.target===this) tutup()"><div class="modal-box"><div id="modalIsi"></div></div></div>  
<script>  
function el(id){return document.getElementById(id)}  
let fotoBaru=[],filterKat='Semua';  
const get=()=>JSON.parse(localStorage.getItem('dok_offline_v2')||'[]');  
const set=v=>localStorage.setItem('dok_offline_v2',JSON.stringify(v));  
el('tgl').valueAsDate=new Date();  
function updateStatus(){const o=navigator.onLine;el('statusDot').innerText=o?'🟢':'🔴';el('offlineBar').classList.toggle('show',!o);}  
window.addEventListener('online',updateStatus);window.addEventListener('offline',updateStatus);updateStatus();  
el('inputFoto').addEventListener('change',e=>{[...e.target.files].forEach(f=>{const r=new FileReader();r.onload=ev=>{fotoBaru.push(ev.target.result);tampilPreview();};r.readAsDataURL(f);});e.target.value='';});  
function tampilPreview(){el('preview').innerHTML=fotoBaru.map((f,i)=>'<div><img src="'+f+'"><button onclick="hapusFotoBaru('+i+',event)">×</button></div>').join('');}  
function hapusFotoBaru(i,ev){ev.stopPropagation();fotoBaru.splice(i,1);tampilPreview();}  
function simpan(){const j=el('judul').value.trim(),t=el('tgl').value,l=el('lokasi').value.trim(),k=el('ket').value.trim(),kat=el('kategori').value;if(!j){alert('Isi Judul dulu!');return;}if(!fotoBaru.length){alert('Pilih minimal 1 foto!');return;}const all=get();all.unshift({id:Date.now(),judul:j,tgl:t,lokasi:l||'-',ket:k||'-',kat,foto:fotoBaru,waktu:new Date().toLocaleString('id-ID')});set(all);el('sukses').style.display='block';el('judul').value='';el('lokasi').value='';el('ket').value='';fotoBaru=[];tampilPreview();render();setTimeout(()=>el('sukses').style.display='none',2000);}  
function setFilter(k,btn){filterKat=k;document.querySelectorAll('.chip').forEach(c=>c.classList.remove('on'));btn.classList.add('on');render();}  
function render(){const all=get(),q=(el('cari').value||'').toLowerCase();const f=all.filter(d=>(filterKat==='Semua'||d.kat===filterKat)&&((d.judul+' '+d.lokasi+' '+d.ket).toLowerCase().includes(q)));el('totalDok').innerText=all.length;el('totalFoto').innerText=all.reduce((a,b)=>a+b.foto.length,0);el('hariIni').innerText=all.filter(d=>d.tgl===new Date().toISOString().slice(0,10)).length;if(!f.length){el('listDok').innerHTML='<div class="card" style="text-align:center">Belum ada dokumentasi.</div>';return;}el('listDok').innerHTML='<div class="grid">'+f.map(d=>'<div class="doc" onclick="buka('+d.id+')"><img src="'+d.foto[0]+'"><div class="doc-body"><span class="badge">'+d.kat+'</span><b>'+d.judul+'</b><small>📅 '+d.tgl+' • 📍 '+d.lokasi+'</small><small>📷 '+d.foto.length+' Foto • '+d.waktu+'</small></div></div>').join('')+'</div>';}  
function buka(id){const d=get().find(x=>x.id===id);if(!d)return;el('modalIsi').innerHTML='<img src="'+d.foto[0]+'"><div class="modal-body"><span class="badge">'+d.kat+'</span><h3 style="margin-top:8px">'+d.judul+'</h3><p style="font-size:13px;color:#475569">📅 '+d.tgl+' • '+d.waktu+'<br>📍 '+d.lokasi+'<br><br>'+d.ket+'</p><div style="display:grid;grid-template-columns:1fr 1fr;gap:8px">'+d.foto.map(f=>'<img src="'+f+'" style="height:120px;object-fit:cover;border-radius:10px" onclick="window.open(this.src)">').join('')+'</div><br><div class="row"><button class="btn btn-gold btn-small" onclick="downloadSatu('+d.id+')">⬇️ Download Foto</button><button class="btn btn-red btn-small" onclick="hapusSatu('+d.id+')">🗑️ Hapus</button></div><button class="btn" style="margin-top:8px" onclick="tutup()">Tutup</button></div>';el('modal').classList.remove('hidden');}  
function tutup(){el('modal').classList.add('hidden');}  
function hapusSatu(id){if(confirm('Hapus dokumentasi ini?')){set(get().filter(x=>x.id!==id));tutup();render();}}  
function hapusSemua(){if(confirm('Hapus SEMUA?')){localStorage.removeItem('dok_offline_v2');render();}}  
function downloadSatu(id){const d=get().find(x=>x.id===id);d.foto.forEach((f,i)=>{const a=document.createElement('a');a.href=f;a.download=d.judul+'-'+(i+1)+'.jpg';a.click();});}  
function downloadExcel(){const all=get();if(!all.length){alert('Belum ada data!');return;}let csv='Tanggal,Waktu,Judul,Kategori,Lokasi,Keterangan,Jumlah Foto\n';all.forEach(d=>{csv+=[d.tgl,d.waktu,'"'+d.judul+'"','"'+d.kat+'"','"'+d.lokasi+'"','"'+d.ket+'"',d.foto.length].join(',')+'\n';});const a=document.createElement('a');a.href=URL.createObjectURL(new Blob(['\uFEFF'+csv],{type:'text/csv'}));a.download='Dokumentasi-Offline.csv';a.click();}  
render();  
</script>  
</body>  
</html>  
