<!DOCTYPE html>
<html lang="vi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1,maximum-scale=1,user-scalable=no">
<title>CRT Generator VIP · Self-Signed X.509</title>
<style>
  *{box-sizing:border-box;-webkit-tap-highlight-color:transparent}
  body{
    margin:0;padding:16px;background:#08080f;color:#e8e8ff;
    font-family:-apple-system,BlinkMacSystemFont,"SF Pro Text","Segoe UI",Roboto,sans-serif;
    min-height:100vh;
    background-image:radial-gradient(circle at 15% 0%,#1a0a3a 0%,transparent 55%),
                     radial-gradient(circle at 85% 100%,#0a1a3a 0%,transparent 55%);
  }
  h1{
    font-size:1.4rem;font-weight:900;letter-spacing:3px;text-align:center;
    background:linear-gradient(90deg,#00f0ff,#ff00c8,#00f0ff);
    -webkit-background-clip:text;background-clip:text;-webkit-text-fill-color:transparent;
    filter:drop-shadow(0 0 10px rgba(0,240,255,.5));
    margin:0 0 6px;
  }
  .sub{font-size:.7rem;color:#8080b0;text-align:center;letter-spacing:2px;margin-bottom:16px;text-transform:uppercase}
  .panel{
    background:rgba(18,18,38,.85);border:1px solid #2a2a5a;border-radius:16px;
    padding:16px;margin-bottom:14px;backdrop-filter:blur(12px);-webkit-backdrop-filter:blur(12px);
    box-shadow:0 0 22px rgba(0,240,255,.08),inset 0 0 22px rgba(0,0,0,.5);
  }
  .panel h2{
    font-size:.75rem;margin:0 0 12px;color:#00f0ff;text-transform:uppercase;
    letter-spacing:2px;display:flex;align-items:center;gap:8px;font-weight:700;
  }
  .panel h2::before{content:'';width:3px;height:14px;background:#ff00c8;border-radius:2px;box-shadow:0 0 10px #ff00c8}
  label{display:block;font-size:.7rem;color:#a0a0d0;margin:10px 0 4px;letter-spacing:.5px}
  input[type=text],input[type=number],textarea,select{
    width:100%;background:#10102a;border:1px solid #2a2a5a;border-radius:10px;
    color:#e8e8ff;font-size:.85rem;padding:10px 12px;outline:none;
    font-family:inherit;transition:border-color .15s,box-shadow .15s;
  }
  input:focus,textarea:focus,select:focus{
    border-color:#00f0ff;box-shadow:0 0 12px rgba(0,240,255,.4);
  }
  textarea{resize:vertical;min-height:70px;font-family:ui-monospace,SFMono-Regular,Menlo,monospace;font-size:.75rem}
  .row{display:flex;gap:10px;flex-wrap:wrap}
  .row > div{flex:1 1 140px}
  .toggle{display:flex;align-items:center;gap:8px;font-size:.8rem;color:#b0b0d8;margin-top:12px}
  .toggle input{width:20px;height:20px;accent-color:#00f0ff}
  button{
    background:linear-gradient(145deg,#1a1a3a,#0d0d22);color:#e8e8ff;
    border:1px solid #2a2a5a;border-radius:11px;padding:12px 14px;
    font-size:.8rem;font-weight:800;cursor:pointer;letter-spacing:1px;
    text-transform:uppercase;width:100%;margin-top:12px;
    box-shadow:0 2px 0 #000,0 0 10px rgba(0,240,255,.1);
    transition:transform .1s,border-color .15s,box-shadow .15s;
  }
  button:active{transform:translateY(2px);box-shadow:0 0 0 #000,0 0 18px #00f0ff;border-color:#00f0ff}
  button.primary{
    background:linear-gradient(145deg,#00d0ff,#0060a0);color:#001018;
    box-shadow:0 0 20px rgba(0,240,255,.5);
  }
  button.primary:active{box-shadow:0 0 32px #00f0ff}
  button.hot{
    background:linear-gradient(145deg,#3a0a20,#18000e);border-color:#ff00c8;
  }
  button.hot:active{box-shadow:0 0 0 #000,0 0 24px #ff00c8}
  .btn-row{display:flex;gap:8px}
  .btn-row > button{flex:1;margin-top:0}
  .out{
    background:#08081a;border:1px solid #1e1e3e;border-radius:10px;
    padding:10px;margin-top:10px;font-family:ui-monospace,SFMono-Regular,Menlo,monospace;
    font-size:.68rem;color:#c8c8f0;white-space:pre-wrap;word-break:break-all;
    max-height:220px;overflow-y:auto;line-height:1.5;
  }
  .status{
    font-size:.75rem;padding:10px 12px;border-radius:10px;margin-top:10px;
    letter-spacing:.5px;line-height:1.4;
  }
  .status.ok{background:rgba(0,255,136,.08);border:1px solid rgba(0,255,136,.3);color:#88ffbb}
  .status.err{background:rgba(255,68,68,.1);border:1px solid rgba(255,68,68,.35);color:#ff8888}
  .status.info{background:rgba(0,240,255,.06);border:1px solid rgba(0,240,255,.25);color:#88e8ff}
  .status.busy{background:rgba(255,180,0,.08);border:1px solid rgba(255,180,0,.3);color:#ffd780}
  .hint{font-size:.65rem;color:#6060a0;margin-top:6px;line-height:1.5}
  .badge{
    display:inline-block;padding:2px 8px;border-radius:20px;
    font-size:.6rem;font-weight:800;letter-spacing:1px;margin-left:6px;
    background:linear-gradient(145deg,#ffd700,#ff6b00);color:#000;
  }
  .steps{font-size:.72rem;color:#b0b0d0;line-height:1.7;padding-left:20px;margin:8px 0 0}
  .steps li{margin-bottom:4px}
</style>
</head>
<body>

<h1>CRT GENERATOR <span style="font-size:.8rem">VIP</span></h1>
<div class="sub">Self-Signed X.509 · RSA · SHA-256 · 100% Client-Side</div>

<div class="panel">
  <h2>Certificate Subject</h2>

  <label>Common Name (CN) *</label>
  <input type="text" id="cn" value="My Root CA" placeholder="example.com hoặc tên bạn">

  <div class="row">
    <div>
      <label>Organization (O)</label>
      <input type="text" id="o" value="My Organization">
    </div>
    <div>
      <label>Org Unit (OU)</label>
      <input type="text" id="ou" value="IT Department">
    </div>
  </div>

  <div class="row">
    <div>
      <label>Country (C) — 2 ký tự</label>
      <input type="text" id="c" value="VN" maxlength="2">
    </div>
    <div>
      <label>State (ST)</label>
      <input type="text" id="st" value="Ho Chi Minh">
    </div>
    <div>
      <label>Locality (L)</label>
      <input type="text" id="l" value="Ho Chi Minh City">
    </div>
  </div>

  <label>Email</label>
  <input type="text" id="email" value="admin@example.com">
</div>

<div class="panel">
  <h2>Options</h2>

  <label>Subject Alternative Name (SAN) — mỗi dòng 1 domain/IP</label>
  <textarea id="san" placeholder="example.com
*.example.com
192.168.1.1"></textarea>
  <div class="hint">Để trống nếu chỉ dùng làm Root CA nội bộ.</div>

  <div class="row">
    <div>
      <label>Hiệu lực (ngày)</label>
      <input type="number" id="days" value="3650" min="1" max="36500">
    </div>
    <div>
      <label>Key size (bit)</label>
      <select id="keySize">
        <option value="2048" selected>2048 (khuyến nghị)</option>
        <option value="3072">3072</option>
        <option value="4096">4096 (chậm hơn)</option>
      </select>
    </div>
  </div>

  <label class="toggle">
    <input type="checkbox" id="isCA" checked>
    Tạo như Root CA (có thể cài làm CA tin cậy)
  </label>
  <div class="hint">Bật = cài vào máy và dùng để ký các cert khác. Tắt = chỉ là cert thường (leaf).</div>

  <button class="primary" id="genBtn">⚡ TẠO CHỨNG CHỈ</button>
  <div id="status" class="status info">Sẵn sàng. Nhấn nút để sinh cặp khóa RSA và ký X.509.</div>
</div>

<div class="panel" id="outPanel" style="display:none">
  <h2>Kết quả <span class="badge">X.509 v3</span></h2>

  <div class="btn-row">
    <button class="hot" id="dlCrt">⬇ Tải .crt</button>
    <button class="hot" id="dlKey">⬇ Tải .key</button>
    <button class="hot" id="copyCrt">📋 Copy CRT</button>
  </div>

  <label>Certificate (PEM)</label>
  <div class="out" id="crtOut"></div>

  <label>Private Key (PEM) — giữ bí mật</label>
  <div class="out" id="keyOut"></div>

  <label>Public Key (PEM)</label>
  <div class="out" id="pubOut"></div>

  <div class="status ok">
    ✅ Đã tạo xong. Bấm <b>Tải .crt</b> để lưu file chứng chỉ.
  </div>
</div>

<div class="panel">
  <h2>Cách cài trên iPhone / iPad</h2>
  <ol class="steps">
    <li>Tải file <b>.crt</b> về máy → mở bằng Files app.</li>
    <li>iOS sẽ hỏi cài profile → bấm <b>Cho phép</b>.</li>
    <li>Vào <b>Cài đặt → Cài đặt chung → VPN &amp; Quản lý thiết bị</b> → chọn profile → <b>Cài đặt</b>.</li>
    <li>Vào <b>Cài đặt → Cài đặt chung → Giới thiệu → Cài đặt tin cậy chứng chỉ</b> → bật công tắc cho cert vừa cài.</li>
    <li>Chứng chỉ giờ đã được tin cậy toàn hệ thống.</li>
  </ol>
  <div class="hint" style="margin-top:8px">⚠️ Chỉ cài cert tự tạo trên máy của chính bạn hoặc máy bạn kiểm soát. Không cài cert của người khác gửi.</div>
</div>

<script>
(function(){
'use strict';

// ============================================================
// ASN.1 / DER ENCODER
// ============================================================
function concat(){
  var len = 0, i;
  for (i = 0; i < arguments.length; i++) len += arguments[i].length;
  var out = new Uint8Array(len);
  var pos = 0;
  for (i = 0; i < arguments.length; i++) {
    out.set(arguments[i], pos);
    pos += arguments[i].length;
  }
  return out;
}

function encodeLen(len){
  if (len < 0x80) return new Uint8Array([len]);
  var bytes = [];
  var v = len;
  while (v > 0) { bytes.unshift(v & 0xff); v = Math.floor(v / 256); }
  return new Uint8Array([0x80 | bytes.length].concat(bytes));
}

function tlv(tag, content){
  var l = encodeLen(content.length);
  var out = new Uint8Array(1 + l.length + content.length);
  out[0] = tag;
  out.set(l, 1);
  out.set(content, 1 + l.length);
  return out;
}

function seq(){ return tlv(0x30, concat.apply(null, arguments)); }
function setOf(){ return tlv(0x31, concat.apply(null, arguments)); }
function ctx(n, content, primitive){
  return tlv((primitive ? 0x80 : 0xa0) | n, content);
}

function integer(bytes){
  var b = bytes;
  var i = 0;
  while (i < b.length - 1 && b[i] === 0) i++;
  b = b.slice(i);
  if (b[0] & 0x80) b = concat(new Uint8Array([0]), b);
  return tlv(0x02, b);
}

function integerFromNumber(n){
  var bytes = [];
  var v = n;
  if (v === 0) bytes.push(0);
  while (v > 0) { bytes.unshift(v & 0xff); v = Math.floor(v / 256); }
  return integer(new Uint8Array(bytes));
}

function boolVal(v){ return tlv(0x01, new Uint8Array([v ? 0xff : 0x00])); }
function nullVal(){ return tlv(0x05, new Uint8Array(0)); }
function octetString(b){ return tlv(0x04, b); }
function bitString(b){ return tlv(0x03, concat(new Uint8Array([0]), b)); }
function utf8(s){ return tlv(0x0C, new TextEncoder().encode(s)); }
function printable(s){ return tlv(0x13, new TextEncoder().encode(s)); }
function ia5(s){ return tlv(0x16, new TextEncoder().encode(s)); }

function oid(str){
  var parts = str.split('.').map(Number);
  var bytes = [40 * parts[0] + parts[1]];
  for (var i = 2; i < parts.length; i++) {
    var v = parts[i];
    var stack = [v & 0x7f];
    v = Math.floor(v / 128);
    while (v > 0) { stack.unshift((v & 0x7f) | 0x80); v = Math.floor(v / 128); }
    for (var j = 0; j < stack.length; j++) bytes.push(stack[j]);
  }
  return tlv(0x06, new Uint8Array(bytes));
}

function pad2(n){ return n < 10 ? '0' + n : '' + n; }

function utcTime(date){
  var s = pad2(date.getUTCFullYear() % 100)
        + pad2(date.getUTCMonth() + 1)
        + pad2(date.getUTCDate())
        + pad2(date.getUTCHours())
        + pad2(date.getUTCMinutes())
        + pad2(date.getUTCSeconds()) + 'Z';
  return tlv(0x17, new TextEncoder().encode(s));
}

function generalizedTime(date){
  var s = String(date.getUTCFullYear()).padStart(4, '0')
        + pad2(date.getUTCMonth() + 1)
        + pad2(date.getUTCDate())
        + pad2(date.getUTCHours())
        + pad2(date.getUTCMinutes())
        + pad2(date.getUTCSeconds()) + 'Z';
  return tlv(0x18, new TextEncoder().encode(s));
}

function timeChoice(date){
  return date.getUTCFullYear() < 2050 ? utcTime(date) : generalizedTime(date);
}

function parseLen(der, pos){
  var b = der[pos];
  if (b < 0x80) return { value: b, end: pos + 1 };
  var n = b & 0x7f;
  var v = 0;
  for (var i = 0; i < n; i++) v = v * 256 + der[pos + 1 + i];
  return { value: v, end: pos + 1 + n };
}

function pemFromDer(der, label){
  var bytes = new Uint8Array(der);
  var bin = '';
  for (var i = 0; i < bytes.length; i++) bin += String.fromCharCode(bytes[i]);
  var b64 = btoa(bin);
  var lines = [];
  for (var k = 0; k < b64.length; k += 64) lines.push(b64.substring(k, k + 64));
  return '-----BEGIN ' + label + '-----\n' + lines.join('\n') + '\n-----END ' + label + '-----';
}

function randomBytes(n){
  var b = new Uint8Array(n);
  crypto.getRandomValues(b);
  return b;
}

function extractPubKeyBytes(spki){
  // SPKI ::= SEQUENCE { AlgorithmIdentifier, BIT STRING }
  var pos = 0;
  if (spki[pos] !== 0x30) throw new Error('SPKI: not SEQUENCE');
  var l = parseLen(spki, pos + 1);
  pos = l.end;
  if (spki[pos] !== 0x30) throw new Error('SPKI: missing AlgId');
  l = parseLen(spki, pos + 1);
  pos = l.end;
  if (spki[pos] !== 0x03) throw new Error('SPKI: missing BIT STRING');
  l = parseLen(spki, pos + 1);
  var contentStart = l.end;
  // First byte = unused bits count (skip it)
  return spki.slice(contentStart + 1, contentStart + l.value);
}

// ============================================================
// CERTIFICATE GENERATION
// ============================================================
async function generateCertificate(opts){
  var cn = opts.cn, o = opts.o, ou = opts.ou, c = opts.c,
      st = opts.st, l = opts.l, email = opts.email,
      san = opts.san, days = opts.days, keySize = opts.keySize, isCA = opts.isCA;

  // 1) Keypair
  var keyPair = await crypto.subtle.generateKey(
    {
      name: 'RSASSA-PKCS1-v1_5',
      modulusLength: keySize,
      publicExponent: new Uint8Array([1, 0, 1]),
      hash: 'SHA-256'
    },
    true,
    ['sign', 'verify']
  );

  // 2) SPKI DER
  var spkiDer = new Uint8Array(await crypto.subtle.exportKey('spki', keyPair.publicKey));

  // 3) SKI = SHA-1 of public key bytes
  var pubKeyBytes = extractPubKeyBytes(spkiDer);
  var skiDigest = new Uint8Array(await crypto.subtle.digest('SHA-1', pubKeyBytes));

  // 4) Name
  function buildName(){
    var rdns = [];
    if (c)      rdns.push(setOf(seq(oid('2.5.4.6'),  printable(c))));
    if (st)     rdns.push(setOf(seq(oid('2.5.4.8'),  utf8(st))));
    if (l)      rdns.push(setOf(seq(oid('2.5.4.7'),  utf8(l))));
    if (o)      rdns.push(setOf(seq(oid('2.5.4.10'), utf8(o))));
    if (ou)     rdns.push(setOf(seq(oid('2.5.4.11'), utf8(ou))));
    if (cn)     rdns.push(setOf(seq(oid('2.5.4.3'),  utf8(cn))));
    if (email)  rdns.push(setOf(seq(oid('1.2.840.113549.1.9.1'), ia5(email))));
    return seq.apply(null, rdns);
  }
  var name = buildName();

  // 5) Validity
  var notBefore = new Date(Date.now() - 24 * 3600 * 1000);
  var notAfter  = new Date(Date.now() + days * 24 * 3600 * 1000);
  var validity = seq(timeChoice(notBefore), timeChoice(notAfter));

  // 6) Serial (16 random bytes, positive)
  var serial = integer(randomBytes(16));

  // 7) AlgorithmIdentifier sha256WithRSAEncryption
  var sigAlg = seq(oid('1.2.840.113549.1.1.11'), nullVal());

  // 8) Extensions
  var extensions = [];

  // 8a) Basic Constraints
  var bcContent = isCA ? seq(boolVal(true)) : seq();
  extensions.push(seq(
    oid('2.5.29.19'),
    boolVal(true),
    octetString(bcContent)
  ));

  // 8b) Key Usage
  var kuBits, kuUnused;
  if (isCA) {
    // digitalSignature(0), keyCertSign(5), cRLSign(6)
    kuBits = new Uint8Array([0x86]);
    kuUnused = 1;
  } else {
    // digitalSignature(0), keyEncipherment(2)
    kuBits = new Uint8Array([0xa0]);
    kuUnused = 5;
  }
  var kuDer = tlv(0x03, concat(new Uint8Array([kuUnused]), kuBits));
  extensions.push(seq(
    oid('2.5.29.15'),
    boolVal(true),
    octetString(kuDer)
  ));

  // 8c) Extended Key Usage
  var ekuDer = seq(
    oid('1.3.6.1.5.5.7.3.1'),  // serverAuth
    oid('1.3.6.1.5.5.7.3.2'),  // clientAuth
    oid('1.3.6.1.5.5.7.3.3')   // codeSigning
  );
  extensions.push(seq(
    oid('2.5.29.37'),
    octetString(ekuDer)
  ));

  // 8d) Subject Key Identifier
  extensions.push(seq(
    oid('2.5.29.14'),
    octetString(octetString(skiDigest))
  ));

  // 8e) Authority Key Identifier (= SKI for self-signed)
  var akiDer = seq(ctx(0, skiDigest, true));
  extensions.push(seq(
    oid('2.5.29.35'),
    octetString(akiDer)
  ));

  // 8f) Subject Alternative Name
  if (san && san.length > 0) {
    var gnList = [];
    for (var i = 0; i < san.length; i++) {
      var s = san[i].trim();
      if (!s) continue;
      if (/^\d+\.\d+\.\d+\.\d+$/.test(s)) {
        var parts = s.split('.').map(Number);
        gnList.push(ctx(7, new Uint8Array(parts), true));
      } else {
        gnList.push(ctx(2, new TextEncoder().encode(s), true));
      }
    }
    if (gnList.length > 0) {
      var sanDer = seq.apply(null, gnList);
      extensions.push(seq(
        oid('2.5.29.17'),
        octetString(sanDer)
      ));
    }
  }

  var extensionsSeq = seq.apply(null, extensions);

  // 9) TBS Certificate
  var version = ctx(0, integerFromNumber(2));
  var tbs = seq(
    version,
    serial,
    sigAlg,
    name,        // issuer
    validity,
    name,        // subject (self-signed)
    spkiDer,
    ctx(3, extensionsSeq)
  );

  // 10) Sign
  var signature = new Uint8Array(await crypto.subtle.sign(
    { name: 'RSASSA-PKCS1-v1_5' },
    keyPair.privateKey,
    tbs
  ));

  // 11) Certificate
  var certDer = seq(
    tbs,
    sigAlg,
    bitString(signature)
  );

  // 12) Private key PEM
  var pkcs8Der = new Uint8Array(await crypto.subtle.exportKey('pkcs8', keyPair.privateKey));

  return {
    certPem: pemFromDer(certDer, 'CERTIFICATE'),
    keyPem:  pemFromDer(pkcs8Der, 'PRIVATE KEY'),
    pubPem:  pemFromDer(spkiDer, 'PUBLIC KEY'),
    certDer: certDer,
    certSize: certDer.length
  };
}

// ============================================================
// UI
// ============================================================
function $(id){ return document.getElementById(id); }

function setStatus(msg, type){
  var el = $('status');
  el.className = 'status ' + (type || 'info');
  el.textContent = msg;
}

function downloadBlob(content, filename){
  var blob = new Blob([content], { type: 'application/x-pem-file' });
  var url = URL.createObjectURL(blob);
  var a = document.createElement('a');
  a.href = url;
  a.download = filename;
  a.rel = 'noopener';
  document.body.appendChild(a);
  a.click();
  setTimeout(function(){
    URL.revokeObjectURL(url);
    document.body.removeChild(a);
  }, 1000);
}

function copyText(text, btn){
  var original = btn.textContent;
  function done(){
    btn.textContent = '✅ ĐÃ COPY';
    setTimeout(function(){ btn.textContent = original; }, 1500);
  }
  function failed(){
    // Fallback: select text in a temp textarea
    var ta = document.createElement('textarea');
    ta.value = text;
    ta.style.position = 'fixed';
    ta.style.top = '-9999px';
    document.body.appendChild(ta);
    ta.select();
    try { document.execCommand('copy'); done(); }
    catch(e) { alert('Không copy được, hãy chọn thủ công trong ô bên dưới.'); }
    document.body.removeChild(ta);
  }
  if (navigator.clipboard && navigator.clipboard.writeText) {
    navigator.clipboard.writeText(text).then(done).catch(failed);
  } else {
    failed();
  }
}

var lastResult = null;

async function onGenerate(){
  // Check crypto.subtle
  if (!window.crypto || !window.crypto.subtle || !window.crypto.subtle.generateKey) {
    setStatus(
      '❌ crypto.subtle không khả dụng. Bạn phải mở file này qua HTTPS hoặc localhost. ' +
      'File:// không được hỗ trợ vì lý do bảo mật của trình duyệt.',
      'err'
    );
    return;
  }

  var cn = $('cn').value.trim();
  if (!cn) { setStatus('❌ Common Name (CN) không được để trống.', 'err'); return; }

  var c = $('c').value.trim().toUpperCase();
  if (c && !/^[A-Z]{2}$/.test(c)) {
    setStatus('❌ Country (C) phải là 2 ký tự chữ (ISO 3166-1 alpha-2).', 'err');
    return;
  }

  var sanText = $('san').value;
  var san = sanText.split('\n').map(function(x){ return x.trim(); }).filter(Boolean);

  var days = parseInt($('days').value, 10);
  if (!days || days < 1) { setStatus('❌ Số ngày hiệu lực không hợp lệ.', 'err'); return; }

  var keySize = parseInt($('keySize').value, 10);
  var isCA = $('isCA').checked;

  $('genBtn').disabled = true;
  setStatus('⏳ Đang sinh cặp khóa RSA ' + keySize + '-bit và ký X.509...', 'busy');

  try {
    var t0 = performance.now();
    var result = await generateCertificate({
      cn: cn, o: $('o').value.trim(), ou: $('ou').value.trim(),
      c: c, st: $('st').value.trim(), l: $('l').value.trim(),
      email: $('email').value.trim(),
      san: san, days: days, keySize: keySize, isCA: isCA
    });
    var dt = Math.round(performance.now() - t0);

    lastResult = result;

    $('crtOut').textContent = result.certPem;
    $('keyOut').textContent = result.keyPem;
    $('pubOut').textContent = result.pubPem;
    $('outPanel').style.display = 'block';

    setStatus('✅ Đã tạo xong trong ' + dt + 'ms · DER size: ' + result.certSize + ' bytes', 'ok');
    $('outPanel').scrollIntoView({ behavior: 'smooth', block: 'start' });
  } catch (err) {
    var msg = err && err.message ? err.message : String(err);
    setStatus('❌ Lỗi: ' + msg, 'err');
    console.error(err);
  } finally {
    $('genBtn').disabled = false;
  }
}

function safeName(s){
  return s.replace(/[^A-Za-z0-9._-]+/g, '_').substring(0, 60) || 'cert';
}

$('genBtn').addEventListener('click', onGenerate);

$('dlCrt').addEventListener('click', function(){
  if (!lastResult) return;
  downloadBlob(lastResult.certPem, safeName($('cn').value) + '.crt');
});

$('dlKey').addEventListener('click', function(){
  if (!lastResult) return;
  downloadBlob(lastResult.keyPem, safeName($('cn').value) + '.key');
});

$('copyCrt').addEventListener('click', function(){
  if (!lastResult) return;
  copyText(lastResult.certPem, this);
});

// Startup check
document.addEventListener('DOMContentLoaded', function(){
  if (!window.crypto || !window.crypto.subtle) {
    setStatus('⚠️ crypto.subtle không có sẵn. Hãy mở trang qua HTTPS hoặc localhost.', 'err');
  }
});

})();
</script>
</body>
</html>
