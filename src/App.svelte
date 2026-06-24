<script>
  import Navbar from './components/Navbar.svelte';
  import Hero from './components/Hero.svelte';
  import Requirements from './components/Requirements.svelte';
  import Pricing from './components/Pricing.svelte';
  
  // Aseguramos que todos los iconos usados abajo estén declarados aquí
  import { 
    Package, 
    ShoppingCart, 
    Truck, 
    BarChart3, 
    Bell, 
    DollarSign, 
    WifiOff 
  } from 'lucide-svelte';

  const coreFeatures = [
    { 
      icon: Package, 
      title: "Gestión de Inventario", 
      description: "Organice su catálogo por categorías, registre productos y mantenga el control absoluto de sus existencias en tiempo real." 
    },
    { 
      // Corregido: Cambiado PointOfSale por ShoppingCart que sí está importado legítimamente
      icon: ShoppingCart, 
      title: "Punto de Venta Integrado", 
      description: "Agilice la atención al cliente. Registre transacciones en segundos, calcule importes de forma automática y consolide las ventas del día." 
    },
    { 
      icon: Truck, 
      title: "Control de Proveedores", 
      description: "Monitoree sus órdenes de abastecimiento y gestione el flujo de mercancía desde el estado de pendiente hasta su recepción en almacén." 
    },
    { 
      icon: BarChart3, 
      title: "Reportes de Utilidad", 
      description: "Obtenga un balance financiero transparente. El sistema calcula el margen neto restando los costos de adquisición de sus ingresos." 
    },
    { 
      icon: Bell, 
      title: "Alertas de Stock Crítico", 
      description: "Evite la pérdida de ventas. Reciba notificaciones automáticas cuando un artículo alcance los niveles mínimos configurados." 
    },
    { 
      icon: DollarSign, 
      title: "Auditoría de Gastos", 
      description: "Registre egresos operativos como servicios públicos, arriendos o transportes para obtener un estado financiero real de su negocio." 
    }
  ];

  function downloadRelease() {
    window.location.href = "https://github.com/bucketpv/stockey/releases";
  }
</script>

<div class="landing-scope">
  <Navbar onDownload={downloadRelease} />
  
  <Hero onDownload={downloadRelease} />

  <section id="features" class="section-padding bg-secondary">
    <div class="content-wrapper">
      <div class="text-center" style="margin-bottom: 60px;">
        <h2 class="section-title">Herramientas esenciales para la operación diaria</h2>
        <p class="section-subtitle">
          Una solución diseñada para optimizar los procesos comerciales de manera ágil, eliminando la necesidad de plataformas complejas o conexiones permanentes a la red.
        </p>
      </div>

      <div class="features-grid">
        {#each coreFeatures as item}
          <div class="feature-card">
            <div class="feature-icon-wrapper">
              <svelte:component this={item.icon} size={22} />
            </div>
            <h3>{item.title}</h3>
            <p>{item.description}</p>
          </div>
        {/each}
      </div>
    </div>
  </section>

  <Requirements />

  <Pricing />

  <section id="arquitectura" class="section-padding">
    <div class="content-wrapper workflow-grid">
      <div class="workflow-text">
        <span class="badge badge-warning"><WifiOff size={12} /> Autonomía Desconectada</span>
        <h2 class="section-title" style="margin-top: 16px; text-align: left;">Privacidad y seguridad por diseño</h2>
        <p style="margin-top: 16px; font-size: 1rem; color: #475569;">
          La información comercial de su empresa le pertenece exclusivamente a usted. Stockey opera resguardando los registros de ventas, costos e inventarios directamente dentro de su equipo, protegiendo su negocio ante caídas masivas de servidores o filtraciones externas de información.
        </p>
        <div class="alert-info-box">
          <span>💡</span>
          <p><strong>Criterio operativo:</strong> La conectividad a internet debe ser un complemento, no una limitación permanente. Valide el sistema y gestione su negocio con total estabilidad.</p>
        </div>
      </div>

      <div class="workflow-visual">
        <h3 style="margin-bottom: 24px; display: flex; align-items: center; gap: 8px; font-size: 1.1rem; color: #0f172a;">
          <Truck size={20} style="color: #2563eb;" /> Flujo de Abastecimiento Comercial
        </h3>
        
        <div class="flow-container">
          <div class="flow-node">
            <span class="node-number muted">1</span>
            <div>
              <h4>Orden Registrada</h4>
              <p>Planificación y consolidación de los productos solicitados al proveedor.</p>
            </div>
          </div>
          <div class="flow-line"></div>
          <div class="flow-node">
            <span class="node-number accent">2</span>
            <div>
              <h4>En Tránsito</h4>
              <p>Seguimiento financiero del pedido mientras se encuentra en ruta de entrega.</p>
            </div>
          </div>
          <div class="flow-line"></div>
          <div class="flow-node">
            <span class="node-number success">3</span>
            <div>
              <h4>Inventariado</h4>
              <p>Actualización e indexación automática de stock al confirmar la recepción en el establecimiento.</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>

  <footer class="footer-container">
    <div class="content-wrapper footer-flex">
      <p>&copy; 2026 Stockey App. Seguridad y soberanía de datos. Optimizado para Windows.</p>
      <span class="badge badge-muted">v1.16.4 Stable</span>
    </div>
  </footer>
</div>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Manrope:wght@400;500;600;700;800&display=swap');

  .landing-scope {
    font-family: 'Manrope', system-ui, sans-serif;
    background: #f8fafc;
    color: #0f172a;
    line-height: 1.6;
    min-height: 100vh;
    width: 100%;
    box-sizing: border-box;
    text-align: left;
    display: flex;
    flex-direction: column;
  }

  .landing-scope :global(.content-wrapper) {
    max-width: 1140px;
    margin: 0 auto;
    padding: 0 24px;
    width: 100%;
    box-sizing: border-box;
  }

  .landing-scope :global(.text-center) {
    text-align: center;
  }

  .landing-scope :global(button),
  .landing-scope :global(.btn-ghost),
  .landing-scope :global(.btn-primary) {
    font-family: 'Manrope', sans-serif;
    cursor: pointer;
    border: none;
    transition: all 0.2s cubic-bezier(0.4, 0, 0.2, 1);
    display: inline-flex;
    align-items: center;
    justify-content: center;
    gap: 8px;
    text-decoration: none;
    box-sizing: border-box;
  }

  .landing-scope :global(.btn-primary) { background: #2563eb; color: #ffffff; font-weight: 600; }
  .landing-scope :global(.btn-primary:hover) { background: #1d4ed8; }
  .landing-scope :global(.btn-glow-effect) { box-shadow: 0 4px 14px rgba(37, 99, 235, 0.4); }
  .landing-scope :global(.btn-glow-effect:hover) { box-shadow: 0 6px 20px rgba(37, 99, 235, 0.6); }

  .landing-scope :global(.btn-ghost) { background: transparent; color: #475569; border: 1px solid #e2e8f0; font-weight: 600; }
  .landing-scope :global(.btn-ghost:hover) { background: #f8fafc; border-color: #cbd5e1; }

  .landing-scope :global(.btn-sm) { padding: 8px 16px; font-size: 0.8rem; border-radius: 6px; height: 36px; }
  .landing-scope :global(.btn-lg) { padding: 12px 24px; font-size: 0.95rem; border-radius: 8px; height: 48px; }

  .landing-scope :global(.badge) { display: inline-flex; align-items: center; gap: 6px; padding: 4px 12px; border-radius: 9999px; font-size: 0.72rem; font-weight: 700; }
  .landing-scope :global(.badge-muted) { background: #ffffff; color: #64748b; border: 1px solid #e2e8f0; }
  .landing-scope :global(.badge-warning) { background: #fffbeb; color: #d97706; }

  .section-padding { padding: 100px 0; width: 100%; }
  .bg-secondary { background: #ffffff; border-top: 1px solid #e2e8f0; border-bottom: 1px solid #e2e8f0; }
  .section-title { font-size: 2.25rem; font-weight: 800; color: #0f172a; letter-spacing: -0.75px; line-height: 1.2; }
  .section-subtitle { font-size: 1.1rem; color: #475569; max-width: 600px; margin: 16px auto 0 auto; }

  .features-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 24px; margin-top: 50px; }
  .feature-card { background: #ffffff; border: 1px solid #e2e8f0; padding: 32px; border-radius: 12px; transition: all 0.2s; text-align: left; }
  .feature-card:hover { transform: translateY(-4px); box-shadow: 0 12px 24px -10px rgba(15, 23, 42, 0.1); border-color: #cbd5e1; }
  .feature-icon-wrapper { width: 44px; height: 44px; background: #eff6ff; color: #2563eb; border-radius: 8px; display: flex; align-items: center; justify-content: center; margin-bottom: 20px; }
  .feature-card h3 { font-size: 1.15rem; font-weight: 700; color: #0f172a; margin-bottom: 10px; }
  .feature-card p { font-size: 0.9rem; color: #475569; line-height: 1.5; }

  .workflow-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 64px; align-items: center; margin-top: 20px; }
  .workflow-visual { background: #ffffff; border: 1px solid #e2e8f0; border-radius: 14px; padding: 40px; box-shadow: 0 4px 12px rgba(15,23,42,0.02); }
  .flow-container { display: flex; flex-direction: column; }
  .flow-node { display: flex; align-items: center; gap: 20px; background: #f8fafc; padding: 16px; border-radius: 10px; border: 1px solid #e2e8f0; text-align: left; }
  .node-number { width: 28px; height: 28px; border-radius: 50%; display: flex; align-items: center; justify-content: center; font-size: 0.8rem; font-weight: 700; flex-shrink: 0; }
  .node-number.muted { background: #e2e8f0; color: #64748b; }
  .node-number.accent { background: #eff6ff; color: #2563eb; }
  .node-number.success { background: #f0fdf4; color: #16a34a; }
  .flow-node h4 { font-size: 0.95rem; font-weight: 700; color: #0f172a; margin-bottom: 2px; }
  .flow-node p { font-size: 0.82rem; color: #475569; }
  .flow-line { width: 2px; height: 20px; background: #cbd5e1; margin-left: 30px; }
  .alert-info-box { margin-top: 28px; background: #eff6ff; padding: 20px; border-radius: 10px; display: flex; gap: 14px; font-size: 0.875rem; color: #1e40af; text-align: left; line-height: 1.5; }

  .footer-container { border-top: 1px solid #e2e8f0; padding: 32px 0; background: #ffffff; font-size: 0.85rem; color: #64748b; margin-top: auto; width: 100%; }
  .footer-flex { display: flex; justify-content: space-between; align-items: center; flex-wrap: wrap; gap: 16px; }

  @media (max-width: 962px) {
    .workflow-grid { grid-template-columns: 1fr; gap: 40px; }
    .section-padding { padding: 60px 0; }
    .section-title { font-size: 1.75rem; }
  }
</style>