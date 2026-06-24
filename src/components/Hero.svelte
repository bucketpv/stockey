<script>
  import { Download } from 'lucide-svelte';
  export let onDownload;
</script>

<section class="hero-section">
  <div class="hero-glow"></div>
  <div class="content-wrapper hero-z text-center">
    <span class="badge badge-cyber">
      Prueba gratuita de 14 días
    </span>
    <h1 class="hero-title">
      <span class="gradient-text">Gestión de inventario.</span><br />
      Sin la nube. Sin lentitud.
    </h1>
    <p class="hero-subtitle">
      Stockey almacena tus datos localmente bajo un entorno híbrido de alto rendimiento.
    </p>
    
    <div class="cta-group">
      <button class="btn-primary btn-lg btn-glow-effect" on:click={onDownload}>
        Descargar para Windows <Download size={18} />
      </button>
    </div>
    <a href="#licencias" class="secondary-link">También puedes ver los planes de licencia →</a>

    <div class="app-mockup-window">
      <div class="mockup-header">
        <div class="mockup-dots">
          <span class="dot red"></span>
          <span class="dot yellow"></span>
          <span class="dot green"></span>
        </div>
        <div class="mockup-title-bar">stockey_core :: live_inventory</div>
      </div>
      <div class="mockup-body">
        <div class="mockup-stats">
          <div class="m-stat"><span class="text-muted-dark">Ventas Hoy:</span> <strong class="text-success-dark">+425.000</strong></div>
          <div class="m-stat"><span class="text-muted-dark">Alertas Stock:</span> <span class="m-alert-badge">3 Críticas</span></div>
        </div>
        <div class="mockup-table">
          <div class="m-tr m-th"><div>ID SKU</div><div>Producto</div><div>Estado</div><div>Stock</div></div>
          <div class="m-tr"><div>STK-092</div><div>Bebida Energética 500ml</div><div><span class="m-badge-ok">Estable</span></div><div class="font-mono">142 u</div></div>
          <div class="m-tr"><div>STK-114</div><div>Café Molido Premium 1kg</div><div><span class="m-badge-warn">Bajo Stock</span></div><div class="font-mono text-warning-dark">8 u</div></div>
        </div>
      </div>
    </div>
  </div>
</section>

<style>
  .hero-section {
    background: #18181c;
    padding: 100px 0;
    position: relative;
    overflow: hidden;
    width: 100%;
  }
  .hero-glow {
    position: absolute;
    top: -20%;
    right: 10%;
    width: 500px;
    height: 500px;
    background: radial-gradient(circle, rgba(37, 99, 235, 0.15) 0%, transparent 75%);
    pointer-events: none;
  }
  .hero-z { 
    position: relative; 
    z-index: 10; 
  }
  .hero-title {
    font-size: 3.5rem;
    font-weight: 800;
    line-height: 1.15;
    letter-spacing: -1.5px;
    color: #ffffff;
    margin-top: 24px;
  }
  .gradient-text {
    background: linear-gradient(to right, #3b82f6, #60a5fa);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
  }
  .hero-subtitle {
    font-size: 1.15rem;
    color: #94a3b8;
    max-width: 680px;
    margin: 24px auto 0 auto;
  }
  .cta-group { 
    display: flex; 
    gap: 16px; 
    justify-content: center; 
    margin: 40px auto 0 auto; 
    flex-wrap: wrap; 
  }
  /* Nuevo estilo para el enlace secundario */
  .secondary-link {
    display: inline-block;
    margin-top: 16px;
    color: #60a5fa;
    font-size: 0.9rem;
    font-weight: 500;
    text-decoration: none;
    border-bottom: 1px solid transparent;
    transition: border-color 0.2s;
  }
  .secondary-link:hover {
    border-color: #60a5fa;
  }
  .badge-cyber { 
    background: rgba(16, 185, 129, 0.1); 
    color: #10b981; 
    border: 1px solid rgba(16, 185, 129, 0.2);
  }
  
  /* MOCKUP WINDOW */
  .app-mockup-window { 
    background: #121214; 
    border: 1px solid #26262b; 
    border-radius: 12px; 
    max-width: 750px; 
    margin: 60px auto 0 auto; 
    box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.5); 
    overflow: hidden; 
  }
  .mockup-header { background: #18181c; padding: 12px 16px; display: flex; align-items: center; border-bottom: 1px solid #26262b; }
  .mockup-dots { display: flex; gap: 6px; }
  .mockup-dots .dot { width: 10px; height: 10px; border-radius: 50%; }
  .dot.red { background: #ef4444; }
  .dot.yellow { background: #f59e0b; }
  .dot.green { background: #10b981; }
  .mockup-title-bar { color: #64748b; font-family: monospace; font-size: 0.75rem; margin-left: 24px; display: flex; align-items: center; }
  .mockup-body { padding: 20px; }
  .mockup-stats { display: flex; gap: 24px; margin-bottom: 16px; font-size: 0.85rem; border-bottom: 1px solid #26262b; padding-bottom: 14px;}
  .text-muted-dark { color: #64748b; }
  .text-success-dark { color: #10b981; font-weight: 700; }
  .m-alert-badge { background: rgba(239, 68, 68, 0.2); color: #ef4444; padding: 2px 8px; border-radius: 4px; font-weight: 600; }
  
  .mockup-table { width: 100%; display: flex; flex-direction: column; font-size: 0.8rem; }
  .m-tr { display: grid; grid-template-columns: 1fr 2fr 1fr 1fr; padding: 10px 8px; color: #f1f5f9; border-bottom: 1px solid rgba(255,255,255,0.02); text-align: left;}
  .m-th { color: #64748b; font-weight: 700; border-bottom: 1px solid #26262b; }
  .m-badge-ok { color: #10b981; background: rgba(16, 185, 129, 0.1); padding: 2px 6px; border-radius: 4px; }
  .m-badge-warn { color: #f59e0b; background: rgba(245, 158, 11, 0.1); padding: 2px 6px; border-radius: 4px; }
  .text-warning-dark { color: #f59e0b; }
  .font-mono { font-family: monospace; }
</style>