 import React, { useState, useEffect } from 'react';
import { Droplets, Wrench, Phone, ChevronDown, ArrowRight, ArrowDown, Gauge, Plane, Plane as Crane, Play, MoveHorizontal, Instagram, Target, Beaker, School, Users } from 'lucide-react';

function App() {
  const [selectedApp, setSelectedApp] = useState<string | null>(null);
  const [force, setForce] = useState(0);
  const [pistonHeight, setPistonHeight] = useState(0);
  const [showGames, setShowGames] = useState(false);
  const [waterLevel, setWaterLevel] = useState(50);
  const [containerPressure, setContainerPressure] = useState(0);
  const [cylinderPosition, setCylinderPosition] = useState(50);
  const [cylinderForce, setCylinderForce] = useState(0);
  
  useEffect(() => {
    const newHeight = Math.min(force * 2, 100);
    setPistonHeight(newHeight);
    const area = 0.5;
    const pressure = (force * 9.81) / area;
    setContainerPressure(pressure);
  }, [force]);

  useEffect(() => {
    const density = 1000;
    const gravity = 9.81;
    const height = waterLevel / 100;
    const pressure = density * gravity * height;
    setContainerPressure(pressure);
  }, [waterLevel]);

  useEffect(() => {
    const maxForce = 1000;
    const force = (cylinderPosition / 100) * maxForce;
    setCylinderForce(force);
  }, [cylinderPosition]);

  const scrollToSection = (id: string) => {
    const element = document.getElementById(id);
    if (element) {
      element.scrollIntoView({ behavior: 'smooth' });
    }
  };

  return (
    <div className="min-h-screen bg-gradient-to-b from-blue-50 to-white">
      {/* Navbar - Updated with new Objetivos link */}
      <nav className="bg-white shadow-md fixed w-full z-50">
        <div className="container mx-auto px-6 py-4 flex items-center justify-between">
          <div className="flex items-center space-x-2">
            <Droplets className="h-8 w-8 text-blue-600" />
            <span className="text-2xl font-bold text-blue-900">Hydrau Tech</span>
          </div>
          <div className="hidden md:flex space-x-8">
            <button onClick={() => scrollToSection('inicio')} className="text-gray-600 hover:text-blue-600">Inicio</button>
            <button onClick={() => scrollToSection('objetivos')} className="text-gray-600 hover:text-blue-600">Objetivos</button>
            <button onClick={() => scrollToSection('aplicaciones')} className="text-gray-600 hover:text-blue-600">Aplicaciones</button>
            <button onClick={() => setShowGames(true)} className="text-gray-600 hover:text-blue-600 flex items-center">
              <Play className="w-4 h-4 mr-2" />
              Juegos Interactivos
            </button>
            <button onClick={() => scrollToSection('contacto')} className="text-gray-600 hover:text-blue-600">Contacto</button>
          </div>
        </div>
      </nav>

      {/* Hero Section */}
      <section id="inicio" className="pt-24 container mx-auto px-6 py-16 md:py-24">
        <div className="max-w-4xl mx-auto text-center">
          <h1 className="text-4xl md:text-6xl font-bold text-blue-900 mb-6">
            Descubre el Poder de la Presión Hidráulica
          </h1>
          <p className="text-xl text-gray-600 mb-8">
            Explorando los principios fundamentales que mueven la industria moderna
          </p>
          <div className="flex justify-center">
            <button 
              onClick={() => scrollToSection('aplicaciones')} 
              className="flex items-center bg-blue-600 text-white px-8 py-3 rounded-full hover:bg-blue-700 transition"
            >
              Aprende más
              <ChevronDown className="ml-2 h-5 w-5" />
            </button>
          </div>
        </div>
      </section>

      {/* NEW: Objetivos Section */}
      <section id="objetivos" className="py-16 bg-white">
        <div className="container mx-auto px-6">
          <h2 className="text-3xl font-bold text-blue-900 mb-12 text-center">Nuestros Objetivos</h2>
          <div className="grid md:grid-cols-3 gap-8 max-w-5xl mx-auto">
            <div className="bg-blue-50 p-6 rounded-xl shadow-lg">
              <div className="flex items-center mb-4">
                <Target className="h-8 w-8 text-blue-600 mr-3" />
                <h3 className="text-xl font-semibold text-blue-800">Educación Interactiva</h3>
              </div>
              <p className="text-gray-600">
                Facilitar el aprendizaje de principios hidráulicos a través de modelos interactivos y simulaciones en tiempo real que permiten la experimentación práctica.
              </p>
            </div>

            <div className="bg-blue-50 p-6 rounded-xl shadow-lg">
              <div className="flex items-center mb-4">
                <Beaker className="h-8 w-8 text-blue-600 mr-3" />
                <h3 className="text-xl font-semibold text-blue-800">Demostración Práctica</h3>
              </div>
              <p className="text-gray-600">
                Mostrar aplicaciones reales de la presión hidráulica mediante ejemplos prácticos y simuladores que replican situaciones del mundo real.
              </p>
            </div>

            <div className="bg-blue-50 p-6 rounded-xl shadow-lg">
              <div className="flex items-center mb-4">
                <School className="h-8 w-8 text-blue-600 mr-3" />
                <h3 className="text-xl font-semibold text-blue-800">Comprensión Profunda</h3>
              </div>
              <p className="text-gray-600">
                Desarrollar una comprensión intuitiva de los principios hidráulicos a través de visualizaciones dinámicas y experimentos controlados.
              </p>
            </div>
          </div>

          <div className="mt-16 bg-gradient-to-r from-blue-100 to-blue-50 rounded-xl p-8 max-w-5xl mx-auto">
            <div className="flex items-start space-x-6">
              <Users className="h-12 w-12 text-blue-600 flex-shrink-0 mt-1" />
              <div>
                <h3 className="text-2xl font-bold text-blue-800 mb-4">Nuestro Compromiso con el Aprendizaje</h3>
                <p className="text-gray-700 mb-6">
                  Nos dedicamos a hacer que los conceptos complejos de la hidráulica sean accesibles para todos. A través de nuestros modelos interactivos, buscamos:
                </p>
                <ul className="space-y-4 text-gray-600">
                  <li className="flex items-center">
                    <div className="h-2 w-2 bg-blue-500 rounded-full mr-3"></div>
                    Visualizar conceptos abstractos de manera tangible
                  </li>
                  <li className="flex items-center">
                    <div className="h-2 w-2 bg-blue-500 rounded-full mr-3"></div>
                    Permitir la experimentación segura y controlada
                  </li>
                  <li className="flex items-center">
                    <div className="h-2 w-2 bg-blue-500 rounded-full mr-3"></div>
                    Conectar la teoría con aplicaciones prácticas
                  </li>
                  <li className="flex items-center">
                    <div className="h-2 w-2 bg-blue-500 rounded-full mr-3"></div>
                    Fomentar el pensamiento crítico y la resolución de problemas
                  </li>
                </ul>
              </div>
            </div>
          </div>
        </div>
      </section>

      {/* ¿Qué es la presión hidráulica? */}
      <section className="bg-white py-16">
        <div className="container mx-auto px-6">
          <div className="max-w-4xl mx-auto">
            <h2 className="text-3xl font-bold text-blue-900 mb-8">¿Qué es la Presión Hidráulica?</h2>
            <div className="grid md:grid-cols-2 gap-12">
              <div>
                <p className="text-gray-600 mb-4">
                  La presión hidráulica es la fuerza ejercida por un fluido sobre una superficie por unidad de área. Este principio fundamental, descubierto por Blaise Pascal, establece que la presión aplicada a un fluido confinado se transmite sin pérdida a todas las partes del fluido y a las paredes del recipiente.
                </p>
                <p className="text-gray-600">
                  El Principio de Pascal, en términos simples, nos dice que si presionamos un líquido en un recipiente cerrado, esta presión se transmite por igual en todas las direcciones.
                </p>
              </div>
              <div className="rounded-lg overflow-hidden shadow-lg">
                <img 
                  src="https://images.unsplash.com/photo-1581092160562-40aa08e78837?auto=format&fit=crop&w=800"
                  alt="Hydraulic system illustration"
                  className="w-full h-full object-cover"
                />
              </div>
            </div>
          </div>
        </div>
      </section>

      {/* Infografías Animadas */}
      <section className="py-16 bg-blue-50">
        <div className="container mx-auto px-6">
          <h2 className="text-3xl font-bold text-blue-900 mb-12 text-center">Principios en Acción</h2>
          
          {/* Principio de Pascal Animado */}
          <div className="max-w-4xl mx-auto mb-16">
            <h3 className="text-2xl font-semibold text-blue-800 mb-6">Principio de Pascal</h3>
            <div className="bg-white p-8 rounded-xl shadow-lg">
              <div className="grid md:grid-cols-2 gap-8 items-center">
                <div className="relative h-64 bg-blue-100 rounded-lg overflow-hidden">
                  <div className="absolute inset-x-0 bottom-0 bg-blue-400 transition-all duration-1000 animate-wave h-32"></div>
                  <div className="absolute inset-0 flex items-center justify-center">
                    <div className="flex space-x-4">
                      <ArrowRight className="h-8 w-8 text-blue-800 animate-pulse" />
                      <ArrowDown className="h-8 w-8 text-blue-800 animate-pulse" />
                      <ArrowRight className="h-8 w-8 text-blue-800 animate-pulse transform rotate-180" />
                    </div>
                  </div>
                </div>
                <div>
                  <p className="text-gray-700">
                    Cuando se aplica presión en cualquier punto de un fluido confinado, esta presión se transmite por igual en todas las direcciones.
                  </p>
                </div>
              </div>
            </div>
          </div>

          {/* Medidor de Presión Animado */}
          <div className="max-w-4xl mx-auto">
            <h3 className="text-2xl font-semibold text-blue-800 mb-6">Medición de Presión</h3>
            <div className="bg-white p-8 rounded-xl shadow-lg">
              <div className="grid md:grid-cols-2 gap-8 items-center">
                <div className="relative h-64 flex items-center justify-center">
                  <div className="relative">
                    <Gauge className="h-32 w-32 text-blue-600" />
                    <div className="absolute top-1/2 left-1/2 h-16 w-1 bg-red-500 transform -translate-x-1/2 -translate-y-1/2 origin-bottom animate-gauge"></div>
                  </div>
                </div>
                <div>
                  <p className="text-gray-700">
                    La presión se mide en unidades como Pascal (Pa), bar o PSI. Los medidores modernos permiten un control preciso de los sistemas hidráulicos.
                  </p>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>

      {/* Interactive Games Modal */}
      {showGames && (
        <div className="fixed inset-0 bg-black bg-opacity-50 z-50 flex items-center justify-center">
          <div className="bg-white rounded-xl p-8 max-w-4xl w-full mx-4 max-h-[90vh] overflow-y-auto">
            <div className="flex justify-between items-center mb-6">
              <h2 className="text-3xl font-bold text-blue-900">Juegos Interactivos</h2>
              <button 
                onClick={() => setShowGames(false)}
                className="text-gray-500 hover:text-gray-700"
              >
                ✕
              </button>
            </div>

            {/* Hydraulic Press Simulator */}
            <div className="mb-12">
              <h3 className="text-2xl font-bold text-blue-800 mb-6">Simulador de Prensa Hidráulica</h3>
              <p className="text-gray-600 mb-4">
                Este simulador demuestra cómo la presión hidráulica se utiliza para multiplicar la fuerza aplicada. 
                Al aumentar la fuerza en el pistón, observarás cómo la presión se transmite a través del fluido.
              </p>
              <div className="bg-blue-50 p-6 rounded-xl">
                <div className="grid md:grid-cols-2 gap-8">
                  <div className="space-y-6">
                    <div>
                      <label className="block text-gray-700 mb-2">
                        Fuerza Aplicada: {force.toFixed(1)} N
                      </label>
                      <input
                        type="range"
                        min="0"
                        max="100"
                        value={force}
                        onChange={(e) => setForce(Number(e.target.value))}
                        className="w-full h-2 bg-blue-200 rounded-lg appearance-none cursor-pointer"
                      />
                    </div>
                    <div className="bg-white p-4 rounded-lg shadow">
                      <p className="text-gray-700">Presión: {containerPressure.toFixed(2)} kPa</p>
                      <p className="text-gray-700">Altura del pistón: {pistonHeight.toFixed(1)} mm</p>
                      <p className="text-gray-700">Trabajo realizado: {(force * pistonHeight / 100).toFixed(2)} J</p>
                    </div>
                  </div>
                  <div className="relative h-64 bg-white rounded-lg shadow-inner">
                    <div className="absolute inset-x-8 bottom-4">
                      <div className="relative h-48 bg-blue-100 rounded">
                        <div
                          className="absolute bottom-0 w-full bg-blue-400 transition-all duration-300"
                          style={{ height: ${pistonHeight}% }}
                        />
                        <div
                          className="absolute w-full h-4 bg-gray-700"
                          style={{ bottom: ${pistonHeight}% }}
                        />
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </div>

            {/* Water Pressure Game */}
            <div className="mb-12">
              <h3 className="text-2xl font-bold text-blue-800 mb-6">Simulador de Presión de Agua</h3>
              <p className="text-gray-600 mb-4">
                Explora cómo la altura de una columna de agua afecta la presión hidrostática. 
                La presión aumenta linealmente con la profundidad debido al peso del agua.
              </p>
              <div className="bg-blue-50 p-6 rounded-xl">
                <div className="grid md:grid-cols-2 gap-8">
                  <div className="space-y-6">
                    <div>
                      <label className="block text-gray-700 mb-2">
                        Nivel de Agua: {waterLevel}%
                      </label>
                      <input
                        type="range"
                        min="0"
                        max="100"
                        value={waterLevel}
                        onChange={(e) => setWaterLevel(Number(e.target.value))}
                        className="w-full h-2 bg-blue-200 rounded-lg appearance-none cursor-pointer"
                      />
                    </div>
                    <div className="bg-white p-4 rounded-lg shadow">
                      <p className="text-gray-700">Presión: {(containerPressure / 1000).toFixed(2)} kPa</p>
                      <p className="text-gray-700">Altura: {(waterLevel / 100).toFixed(2)} m</p>
                      <p className="text-gray-700">Volumen: {((waterLevel / 100) * 1000).toFixed(2)} L</p>
                    </div>
                  </div>
                  <div className="relative h-64 bg-white rounded-lg shadow-inner">
                    <div className="absolute inset-x-8 bottom-4">
                      <div className="relative h-48 bg-blue-100 rounded overflow-hidden">
                        <div
                          className="absolute bottom-0 w-full bg-blue-400 transition-all duration-300"
                          style={{ height: ${waterLevel}% }}
                        >
                          <div className="absolute inset-0 animate-wave opacity-30 bg-blue-300" />
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </div>

            {/* Hydraulic Cylinder Game */}
            <div>
              <h3 className="text-2xl font-bold text-blue-800 mb-6">Cilindro Hidráulico</h3>
              <p className="text-gray-600 mb-4">
                Controla un cilindro hidráulico y observa cómo la presión del fluido se convierte en movimiento lineal. 
                Este principio es fundamental en maquinaria pesada y sistemas de control.
              </p>
              <div className="bg-blue-50 p-6 rounded-xl">
                <div className="grid md:grid-cols-2 gap-8">
                  <div className="space-y-6">
                    <div>
                      <label className="block text-gray-700 mb-2">
                        Posición del Cilindro: {cylinderPosition}%
                      </label>
                      <input
                        type="range"
                        min="0"
                        max="100"
                        value={cylinderPosition}
                        onChange={(e) => setCylinderPosition(Number(e.target.value))}
                        className="w-full h-2 bg-blue-200 rounded-lg appearance-none cursor-pointer"
                      />
                    </div>
                    <div className="bg-white p-4 rounded-lg shadow">
                      <p className="text-gray-700">Fuerza: {cylinderForce.toFixed(2)} N</p>
                      <p className="text-gray-700">Presión: {(cylinderForce / 0.3).toFixed(2)} kPa</p>
                      <p className="text-gray-700">Extensión: {(cylinderPosition / 100 * 500).toFixed(1)} mm</p>
                    </div>
                  </div>
                  <div className="relative h-64 bg-white rounded-lg shadow-inner">
                    <div className="absolute inset-y-0 inset-x-8 flex items-center">
                      <div className="relative w-full h-16 bg-blue-100 rounded-lg overflow-hidden">
                        <div className="absolute inset-y-0 left-0 bg-blue-400 transition-all duration-300 flex items-center"
                             style={{ width: ${cylinderPosition}% }}>
                          <MoveHorizontal className="h-8 w-8 text-blue-800 ml-2" />
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      )}

      {/* Aplicaciones */}
      <section id="aplicaciones" className="py-16 bg-gray-50">
        <div className="container mx-auto px-6">
          <h2 className="text-3xl font-bold text-blue-900 mb-12 text-center">Aplicaciones en la Vida Real</h2>
          <div className="grid md:grid-cols-2 lg:grid-cols-4 gap-8">
            {/* Frenos de autos */}
            <div 
              className={bg-white p-6 rounded-lg shadow-md cursor-pointer transition-all duration-300 ${selectedApp === 'frenos' ? 'ring-2 ring-blue-500' : 'hover:shadow-xl'}}
              onClick={() => setSelectedApp('frenos')}
            >
              <Wrench className="h-12 w-12 text-blue-600 mb-4" />
              <h3 className="text-xl font-semibold mb-3">Frenos Hidráulicos</h3>
              <img 
                src="https://images.unsplash.com/photo-1486262715619-67b85e0b08d3?auto=format&fit=crop&w=800&q=80"
                alt="Sistema de frenos"
                className="w-full h-48 object-cover rounded-lg mb-4"
              />
              <p className="text-gray-600">
                Los sistemas de frenos modernos utilizan la presión hidráulica para multiplicar la fuerza aplicada al pedal del freno, permitiendo detener vehículos pesados con un esfuerzo mínimo.
              </p>
            </div>

            {/* Grúas */}
            <div 
              className={bg-white p-6 rounded-lg shadow-md cursor-pointer transition-all duration-300 ${selectedApp === 'gruas' ? 'ring-2 ring-blue-500' : 'hover:shadow-xl'}}
              onClick={() => setSelectedApp('gruas')}
            >
              <Crane className="h-12 w-12 text-blue-600 mb-4" />
              <h3 className="text-xl font-semibold mb-3">Grúas Hidráulicas</h3>
              <img 
                src="https://images.unsplash.com/photo-1504307651254-35680f356dfd?auto=format&fit=crop&w=800&q=80"
                alt="Grúa hidráulica"
                className="w-full h-48 object-cover rounded-lg mb-4"
              />
              <p className="text-gray-600">
                Las grúas hidráulicas pueden levantar cargas extremadamente pesadas gracias a la multiplicación de fuerza que proporciona el sistema hidráulico.
              </p>
            </div>

            {/* Prensas */}
            <div 
              className={bg-white p-6 rounded-lg shadow-md cursor-pointer transition-all duration-300 ${selectedApp === 'prensas' ? 'ring-2 ring-blue-500' : 'hover:shadow-xl'}}
              onClick={() => setSelectedApp('prensas')}
            >
              <Wrench className="h-12 w-12 text-blue-600 mb-4" />
              <h3 className="text-xl font-semibold mb-3">Prensas Industriales</h3>
              <img 
                src="https://images.unsplash.com/photo-1590846406792-0adc7f938f1d?auto=format&fit=crop&w=800&q=80"
                alt="Prensa industrial"
                className="w-full h-48 object-cover rounded-lg mb-4"
              />
              <p className="text-gray-600">
                Las prensas hidráulicas son fundamentales en la fabricación y el conformado de metales, permitiendo aplicar fuerzas enormes de manera controlada.
              </p>
            </div>

            {/* Aviones */}
            <div 
              className={bg-white p-6 rounded-lg shadow-md cursor-pointer transition-all duration-300 ${selectedApp === 'aviones' ? 'ring-2 ring-blue-500' : 'hover:shadow-xl'}}
              onClick={() => setSelectedApp('aviones')}
            >
              <Plane className="h-12 w-12 text-blue-600 mb-4" />
              <h3 className="text-xl font-semibold mb-3">Sistemas Aeronáuticos</h3>
              <img 
                src="https://images.unsplash.com/photo-1436491865332-7a61a109cc05?auto=format&fit=crop&w=800&q=80"
                alt="Sistema hidráulico en avión"
                className="w-full h-48 object-cover rounded-lg mb-4"
              />
              <p className="text-gray-600">
                Los aviones utilizan sistemas hidráulicos para el control de superficies de vuelo, tren de aterrizaje y otros sistemas críticos.
              </p>
            </div>
          </div>

          {selectedApp && (
            <div className="mt-8 p-6 bg-white rounded-lg shadow-lg">
              <button 
                onClick={() => setSelectedApp(null)}
                className="text-blue-600 hover:text-blue-800 mb-4"
              >
                ← Volver
              </button>
              <div className="prose max-w-none">
                {selectedApp === 'frenos' && (
                  <div>
                    <h3 className="text-2xl font-bold mb-4">Sistema de Frenos Hidráulicos</h3>
                    <p>Los frenos hidráulicos funcionan mediante la transmisión de fuerza a través de un fluido incompresible. Cuando el conductor presiona el pedal del freno, esta fuerza se multiplica y se distribuye uniformemente a cada rueda.</p>
                  </div>
                )}
                {selectedApp === 'gruas' && (
                  <div>
                    <h3 className="text-2xl font-bold mb-4">Grúas Hidráulicas</h3>
                    <p>Las grúas hidráulicas utilizan cilindros hidráulicos para levantar y mover cargas pesadas. La presión hidráulica permite que una fuerza relativamente pequeña levante objetos extremadamente pesados.</p>
                  </div>
                )}
                {selectedApp === 'prensas' && (
                  <div>
                    <h3 className="text-2xl font-bold mb-4">Prensas Hidráulicas Industriales</h3>
                    <p>Las prensas hidráulicas son máquinas que utilizan la presión hidráulica para comprimir materiales. Son esenciales en la fabricación de automóviles, la formación de metales y muchos otros procesos industriales.</p>
                  </div>
                )}
                {selectedApp === 'aviones' && (
                  <div>
                    <h3 className="text-2xl font-bold text-blue-800 mb-4">Sistemas Hidráulicos en Aviación</h3>
                    <p>Los sistemas hidráulicos son cruciales en la aviación moderna. Se utilizan para el control de superficies de vuelo, el despliegue y retracción del tren de aterrizaje, y los sistemas de frenado.</p>
                  </div>
                )}
              </div>
            </div>
          )}
        </div>
      </section>

      {/* Contacto */}
      <section id="contacto" className="py-16 bg-blue-900 text-white">
        <div className="container mx-auto px-6">
          <div className="max-w-4xl mx-auto text-center">
            <h2 className="text-3xl font-bold mb-8">Contacto</h2>
            <div className="flex flex-col items-center justify-center space-y-4 mb-8">
              <div className="flex items-center space-x-4">
                <Phone className="h-6 w-6" />
                <span>+52 477 123 4567</span>
              </div>
              <div className="flex items-center space-x-4">
                <Instagram className="h-6 w-6" />
                <a 
                  href="https://instagram.com/hydru.tech" 
                  target="_blank" 
                  rel="noopener noreferrer"
                  className="hover:text-blue-200 transition-colors"
                >
                  @hydru.tech
                </a>
              </div>
            </div>
            <p className="text-blue-200">
              ©️ 2025 Hydrau Tech. Todos los derechos reservados.
            </p>
          </div>
        </div>
      </section>
    </div>
  );
}

export default App;
