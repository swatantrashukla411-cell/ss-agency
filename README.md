import React, { useState, useEffect } from 'react';
import { motion, AnimatePresence, useScroll, useSpring } from 'framer-motion';
import { 
  Phone, 
  MapPin, 
  TrendingUp, 
  Users, 
  Search, 
  Target, 
  CheckCircle2, 
  ArrowRight, 
  Instagram, 
  Facebook, 
  Smartphone, 
  ShoppingBag, 
  Hospital,
  Store,
  ChevronRight,
  MessageCircle,
  BarChart3
} from 'lucide-react';

// --- Components ---

const Navbar = () => (
  <nav className="fixed top-0 left-0 right-0 z-50 bg-slate-950/80 backdrop-blur-md border-b border-slate-800">
    <div className="max-w-7xl mx-auto px-4 h-20 flex items-center justify-between">
      <div className="flex items-center gap-2">
        <div className="w-10 h-10 bg-blue-600 rounded-lg flex items-center justify-center font-bold text-2xl">SS</div>
        <span className="text-xl font-bold tracking-tighter">AGENCY</span>
      </div>
      <div className="hidden md:flex gap-8 text-sm font-medium text-slate-300">
        <a href="#problem" className="hover:text-blue-500 transition-colors">The Problem</a>
        <a href="#solution" className="hover:text-blue-500 transition-colors">Our Solution</a>
        <a href="#services" className="hover:text-blue-500 transition-colors">Services</a>
        <a href="#founder" className="hover:text-blue-500 transition-colors">Founder</a>
      </div>
      <a 
        href="tel:9532792303" 
        className="bg-blue-600 hover:bg-blue-700 text-white px-6 py-2 rounded-full font-bold flex items-center gap-2 transition-all"
      >
        <Phone size={18} /> 9532792303
      </a>
    </div>
  </nav>
);

const Hero = () => {
  return (
    <section className="relative min-h-screen pt-32 pb-20 flex flex-col items-center justify-center overflow-hidden">
      {/* Background Decor */}
      <div className="absolute top-1/4 -left-20 w-96 h-96 bg-blue-600/10 rounded-full blur-[120px]" />
      <div className="absolute bottom-1/4 -right-20 w-96 h-96 bg-purple-600/10 rounded-full blur-[120px]" />

      <div className="max-w-7xl mx-auto px-4 grid lg:grid-cols-2 gap-12 items-center">
        <motion.div 
          initial={{ opacity: 0, x: -50 }}
          animate={{ opacity: 1, x: 0 }}
          transition={{ duration: 0.8 }}
        >
          <div className="inline-block px-4 py-1.5 mb-6 rounded-full bg-blue-500/10 border border-blue-500/20 text-blue-400 text-sm font-semibold uppercase tracking-wider">
            Transforming Local Businesses
          </div>
          <h1 className="text-5xl md:text-7xl font-extrabold leading-tight mb-6">
            Aapka Business Achha Hai… <br />
            <span className="text-transparent bg-clip-text bg-gradient-to-r from-blue-400 to-blue-600">
              Lekin Customers Kahan Hain?
            </span>
          </h1>
          <p className="text-xl text-slate-400 mb-8 max-w-xl leading-relaxed">
            Local shops, hospitals aur restaurants ke liye banayi gayi special digital marketing. Hum followers nahi, <span className="text-white font-bold italic">Asli Customers</span> dete hain.
          </p>
          <div className="flex flex-col sm:flex-row gap-4">
            <motion.a 
              whileHover={{ scale: 1.05 }}
              whileTap={{ scale: 0.95 }}
              href="#problem"
              className="px-8 py-4 bg-blue-600 rounded-xl font-bold text-lg flex items-center justify-center gap-2 shadow-lg shadow-blue-600/20"
            >
              See the Real Problem <ArrowRight size={20} />
            </motion.a>
          </div>
        </motion.div>

        <motion.div 
          initial={{ opacity: 0, scale: 0.8 }}
          animate={{ opacity: 1, scale: 1 }}
          transition={{ duration: 1, delay: 0.2 }}
          className="relative"
        >
          {/* Visual Animation: Empty Shop */}
          <div className="relative z-10 bg-slate-900 border border-slate-800 rounded-3xl p-8 shadow-2xl">
            <div className="flex justify-between items-center mb-8 border-b border-slate-800 pb-4">
              <div className="flex gap-4">
                <div className="w-12 h-12 bg-slate-800 rounded-lg flex items-center justify-center text-slate-400">
                  <Store />
                </div>
                <div>
                  <div className="h-4 w-32 bg-slate-800 rounded mb-2"></div>
                  <div className="h-3 w-20 bg-slate-800/50 rounded"></div>
                </div>
              </div>
              <div className="text-red-500 font-bold text-sm bg-red-500/10 px-3 py-1 rounded-full">No Footfall</div>
            </div>
            
            <div className="grid grid-cols-3 gap-4 mb-8">
              {[1,2,3].map(i => (
                <div key={i} className="aspect-square bg-slate-800/30 rounded-xl border border-dashed border-slate-700 flex items-center justify-center text-slate-600">
                  <ShoppingBag size={24} />
                </div>
              ))}
            </div>

            <div className="bg-slate-950 rounded-2xl p-6 text-center border border-slate-800">
              <p className="text-slate-400 text-sm mb-4 italic">"Sab kuch sahi hai, phir bhi grahak nahi aa rahe..."</p>
              <div className="flex justify-center gap-2">
                {[1,2,3,4,5].map(i => <div key={i} className="w-2 h-2 rounded-full bg-slate-800" />)}
              </div>
            </div>
          </div>
          
          {/* Decorative Floating Elements */}
          <motion.div 
            animate={{ y: [0, -20, 0] }}
            transition={{ duration: 4, repeat: Infinity }}
            className="absolute -top-10 -right-10 w-24 h-24 bg-blue-600/20 rounded-2xl backdrop-blur-xl border border-blue-500/30 flex items-center justify-center"
          >
            <TrendingUp className="text-blue-500" size={40} />
          </motion.div>
        </motion.div>
      </div>
    </section>
  );
};

const ProblemSection = () => {
  const problems = [
    { icon: <Search className="text-red-400" />, title: "Not on Google", desc: "Log search karte hain par aapka business nahi dikhta." },
    { icon: <Smartphone className="text-red-400" />, title: "Dead Social Media", desc: "ID toh hai, par wahan se ek bhi customer nahi aata." },
    { icon: <Target className="text-red-400" />, title: "No New Leads", desc: "Sirf purane grahak ya word-of-mouth pe dependence." },
    { icon: <TrendingUp className="text-red-400" />, title: "Competitor Growth", desc: "Pados wali dukan/clinic online zyada patients le rahi hai." },
  ];

  return (
    <section id="problem" className="py-24 bg-slate-950">
      <div className="max-w-7xl mx-auto px-4">
        <div className="text-center mb-16">
          <h2 className="text-3xl md:text-5xl font-bold mb-6">Business Offline Hai,<br /> <span className="text-blue-500 underline decoration-red-500/50 underline-offset-8">Lekin Duniya Online Ho Chuki Hai.</span></h2>
          <p className="text-slate-400 text-lg max-w-2xl mx-auto">Agar koi aapko internet par dhoond nahi sakta, toh woh aapka customer kabhi ban hi nahi sakta.</p>
        </div>

        <div className="grid md:grid-cols-2 lg:grid-cols-4 gap-6">
          {problems.map((p, idx) => (
            <motion.div 
              key={idx}
              whileHover={{ y: -10 }}
              className="p-8 rounded-3xl bg-slate-900 border border-slate-800 hover:border-red-500/30 transition-all group"
            >
              <div className="w-14 h-14 rounded-2xl bg-slate-800 flex items-center justify-center mb-6 group-hover:bg-red-500/10 transition-colors">
                {p.icon}
              </div>
              <h3 className="text-xl font-bold mb-3">{p.title}</h3>
              <p className="text-slate-400 leading-relaxed">{p.desc}</p>
            </motion.div>
          ))}
        </div>
      </div>
    </section>
  );
};

const TransformationSection = () => {
  const [active, setActive] = useState(false);

  return (
    <section className="py-24 bg-slate-900 overflow-hidden">
      <div className="max-w-7xl mx-auto px-4">
        <div className="grid lg:grid-cols-2 gap-16 items-center">
          <div>
            <h2 className="text-4xl font-bold mb-8 leading-tight">Magic of Digital Marketing:<br /> <span className="text-blue-500">Khaali Dukan se Line Tak ka Safar.</span></h2>
            
            <div className="space-y-6">
              <div className="flex gap-4 items-start">
                <div className="mt-1 bg-green-500/20 p-1 rounded-full"><CheckCircle2 className="text-green-500" size={18} /></div>
                <div>
                  <h4 className="font-bold text-lg">Google Search = New Customers</h4>
                  <p className="text-slate-400">Log search karenge "Best Hospital near me" aur aap dikhenge top par.</p>
                </div>
              </div>
              <div className="flex gap-4 items-start">
                <div className="mt-1 bg-green-500/20 p-1 rounded-full"><CheckCircle2 className="text-green-500" size={18} /></div>
                <div>
                  <h4 className="font-bold text-lg">Instagram/FB = Daily Leads</h4>
                  <p className="text-slate-400">Rozana log aapke services ke baare mein inquire karenge.</p>
                </div>
              </div>
              <div className="flex gap-4 items-start">
                <div className="mt-1 bg-green-500/20 p-1 rounded-full"><CheckCircle2 className="text-green-500" size={18} /></div>
                <div>
                  <h4 className="font-bold text-lg">Trust + Growth</h4>
                  <p className="text-slate-400">Professional branding se grahak ka vishwas badhta hai.</p>
                </div>
              </div>
            </div>
          </div>

          <div className="relative">
            <div 
              className="cursor-pointer relative z-10 bg-slate-950 border border-slate-800 rounded-3xl p-1 overflow-hidden"
              onClick={() => setActive(!active)}
            >
              <div className="flex bg-slate-900 rounded-2xl mb-1">
                <button className={`flex-1 py-3 font-bold transition-all ${!active ? 'bg-blue-600 text-white' : 'text-slate-500'}`}>Before (Problems)</button>
                <button className={`flex-1 py-3 font-bold transition-all ${active ? 'bg-green-600 text-white' : 'text-slate-500'}`}>After (Success)</button>
              </div>

              <div className="p-8 h-[350px] flex flex-col items-center justify-center text-center">
                <AnimatePresence mode="wait">
                  {!active ? (
                    <motion.div 
                      key="before"
                      initial={{ opacity: 0, scale: 0.9 }}
                      animate={{ opacity: 1, scale: 1 }}
                      exit={{ opacity: 0, scale: 0.9 }}
                      className="space-y-4"
                    >
                      <div className="w-20 h-20 bg-slate-800 rounded-full flex items-center justify-center mx-auto text-slate-500">
                        <Users size={40} />
                      </div>
                      <h3 className="text-2xl font-bold">Khaali Waitroom</h3>
                      <p className="text-slate-400">No calls, no messages, zero visitors from internet.</p>
                    </motion.div>
                  ) : (
                    <motion.div 
                      key="after"
                      initial={{ opacity: 0, scale: 0.9 }}
                      animate={{ opacity: 1, scale: 1 }}
                      exit={{ opacity: 0, scale: 0.9 }}
                      className="space-y-4"
                    >
                      <div className="relative">
                        <motion.div 
                          animate={{ scale: [1, 1.2, 1] }}
                          transition={{ repeat: Infinity, duration: 2 }}
                          className="w-20 h-20 bg-green-500/20 rounded-full flex items-center justify-center mx-auto text-green-500"
                        >
                          <MessageCircle size={40} />
                        </motion.div>
                        <div className="absolute -top-2 -right-2 bg-red-500 text-[10px] font-bold px-2 py-0.5 rounded-full">+15 Leads Today</div>
                      </div>
                      <h3 className="text-2xl font-bold text-green-500">Busy Business!</h3>
                      <p className="text-slate-400">Non-stop inquiries, bookings and real growth.</p>
                    </motion.div>
                  )}
                </AnimatePresence>
              </div>
            </div>
            
            <div className="absolute -bottom-6 -left-6 w-full h-full bg-blue-600/5 -z-0 rounded-3xl border border-blue-600/10" />
          </div>
        </div>
      </div>
    </section>
  );
};

const StepsSection = () => {
  const steps = [
    { title: "Business Analysis", desc: "Hum aapke local area aur competitors ko check karte hain." },
    { title: "GMB Optimization", desc: "Google My Business setup taaki aap Google Map pe sabse upar dikhein." },
    { title: "Social Media Boost", desc: "Instagram aur Facebook page ko professional look dena." },
    { title: "Targeted Paid Ads", desc: "Sirf aapke area ke logon ko aapki dukan ke ads dikhana." },
    { title: "Lead Tracking", desc: "Aapko har din reports milengi ki kitne grahak aaye." },
    { title: "Scale Strategy", desc: "Dhire dhire business ko city-wide grow karna." },
  ];

  return (
    <section id="solution" className="py-24 bg-slate-950">
      <div className="max-w-7xl mx-auto px-4">
        <div className="text-center mb-20">
          <h2 className="text-3xl md:text-5xl font-bold mb-4">SS Agency Ka Step-by-Step Solution</h2>
          <p className="text-slate-400">Humein pata hai local business kaise chalta hai. Zero complications.</p>
        </div>

        <div className="relative">
          {/* Timeline Line */}
          <div className="hidden lg:block absolute left-1/2 top-0 bottom-0 w-1 bg-slate-800 -translate-x-1/2 rounded-full" />

          <div className="space-y-12 relative">
            {steps.map((s, idx) => (
              <motion.div 
                key={idx}
                initial={{ opacity: 0, y: 20 }}
                whileInView={{ opacity: 1, y: 0 }}
                viewport={{ once: true }}
                className={`flex flex-col lg:flex-row items-center gap-8 ${idx % 2 !== 0 ? 'lg:flex-row-reverse' : ''}`}
              >
                <div className="flex-1 text-center lg:text-left lg:px-12">
                  <div className={`inline-flex items-center justify-center w-12 h-12 rounded-xl bg-blue-600 text-white font-bold text-xl mb-4 ${idx % 2 !== 0 ? 'lg:ml-auto' : ''}`}>
                    {idx + 1}
                  </div>
                  <h3 className={`text-2xl font-bold mb-3 ${idx % 2 !== 0 ? 'lg:text-right' : ''}`}>{s.title}</h3>
                  <p className={`text-slate-400 ${idx % 2 !== 0 ? 'lg:text-right' : ''}`}>{s.desc}</p>
                </div>
                
                <div className="z-10 w-10 h-10 rounded-full bg-slate-950 border-4 border-blue-600 shadow-lg shadow-blue-600/40 hidden lg:block" />
                
                <div className="flex-1 hidden lg:block" />
              </motion.div>
            ))}
          </div>
        </div>
      </div>
    </section>
  );
};

const ServicesSection = () => {
  const services = [
    { icon: <MapPin />, title: "GMB Optimization", tag: "Most Popular" },
    { icon: <Instagram />, title: "Social Media Ads", tag: "High Leads" },
    { icon: <Search />, title: "Local SEO Specialist", tag: "Top Ranking" },
    { icon: <Hospital />, title: "Clinic & Hospital Marketing", tag: "Specialized" },
    { icon: <Smartphone />, title: "Lead Generation", tag: "Direct Sales" },
    { icon: <BarChart3 />, title: "Business Branding", tag: "Premium" },
  ];

  return (
    <section id="services" className="py-24 bg-slate-900">
      <div className="max-w-7xl mx-auto px-4">
        <div className="flex flex-col md:flex-row md:items-end justify-between mb-16 gap-6">
          <div>
            <h2 className="text-4xl font-bold mb-4">Our Core Services</h2>
            <p className="text-slate-400">Har service ka ek hi maqsad - More Footfall.</p>
          </div>
          <a href="tel:9532792303" className="text-blue-500 font-bold flex items-center gap-2 group">
            All Services <ChevronRight className="group-hover:translate-x-1 transition-transform" />
          </a>
        </div>

        <div className="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6">
          {services.map((s, idx) => (
            <motion.div 
              key={idx}
              whileHover={{ scale: 1.02 }}
              className="p-1 rounded-3xl bg-gradient-to-br from-slate-800 to-slate-900 group border border-slate-800"
            >
              <div className="p-8 bg-slate-950 rounded-[22px] h-full flex flex-col items-start">
                <div className="mb-4 text-xs font-bold text-blue-500 bg-blue-500/10 px-3 py-1 rounded-full uppercase tracking-tighter">
                  {s.tag}
                </div>
                <div className="w-12 h-12 bg-blue-600 rounded-2xl flex items-center justify-center text-white mb-6 group-hover:scale-110 transition-transform">
                  {s.icon}
                </div>
                <h3 className="text-2xl font-bold mb-4">{s.title}</h3>
                <div className="mt-auto flex items-center text-slate-500 font-medium group-hover:text-white transition-colors">
                  Learn More <ChevronRight size={16} className="ml-1" />
                </div>
              </div>
            </motion.div>
          ))}
        </div>
      </div>
    </section>
  );
};

const FounderSection = () => (
  <section id="founder" className="py-24 bg-slate-950">
    <div className="max-w-7xl mx-auto px-4">
      <div className="bg-slate-900 rounded-[40px] p-8 md:p-16 border border-slate-800 flex flex-col lg:flex-row gap-12 items-center">
        <div className="w-48 h-48 md:w-64 md:h-64 rounded-3xl overflow-hidden bg-blue-600 flex-shrink-0 border-4 border-slate-800 shadow-2xl">
          {/* Placeholder for Founder Photo */}
          <div className="w-full h-full flex items-center justify-center text-white text-6xl font-black">SS</div>
        </div>
        <div>
          <h2 className="text-4xl font-bold mb-2">Swatantra Shukla</h2>
          <p className="text-blue-500 font-bold mb-6 text-xl">Founder, SS Agency</p>
          <blockquote className="text-2xl italic text-slate-300 mb-8 leading-relaxed">
            "Mera mission hai local business owners ko wo respect aur growth dilaana jiske wo haqdaar hain. Digital marketing sirf bade brands ke liye nahi, aapke liye bhi hai."
          </blockquote>
          <div className="flex gap-4">
            <div className="flex items-center gap-2 text-slate-400"><CheckCircle2 size={18} className="text-blue-500" /> 5+ Years Experience</div>
            <div className="flex items-center gap-2 text-slate-400"><CheckCircle2 size={18} className="text-blue-500" /> Local Market Expert</div>
          </div>
        </div>
      </div>
    </div>
  </section>
);

const Footer = () => (
  <footer className="bg-slate-950 pt-24 pb-12 border-t border-slate-900">
    <div className="max-w-7xl mx-auto px-4">
      <div className="text-center mb-16">
        <motion.div 
          initial={{ opacity: 0 }}
          whileInView={{ opacity: 1 }}
          className="bg-blue-600/10 border border-blue-500/20 rounded-[40px] p-12 md:p-20 mb-16 relative overflow-hidden"
        >
          <div className="absolute top-0 right-0 p-8 opacity-10"><TrendingUp size={120} /></div>
          <h2 className="text-4xl md:text-6xl font-black mb-8">Grahak Chahiye?<br /> To Aaj Hi Baat Karein.</h2>
          <p className="text-xl text-slate-400 mb-10 max-w-2xl mx-auto">Free Consultation Call book karein aur jaanein aapka business kaise grow karega.</p>
          
          <div className="flex flex-col sm:flex-row items-center justify-center gap-6">
            <motion.a 
              whileHover={{ scale: 1.05 }}
              whileTap={{ scale: 0.95 }}
              href="tel:9532792303" 
              className="w-full sm:w-auto px-10 py-5 bg-blue-600 text-white rounded-2xl font-black text-2xl flex items-center justify-center gap-3 shadow-xl shadow-blue-600/30"
            >
              <Phone size={28} fill="currentColor" /> Call: 9532792303
            </motion.a>
            <motion.a 
              whileHover={{ scale: 1.05 }}
              whileTap={{ scale: 0.95 }}
              href="https://wa.me/919532792303" 
              className="w-full sm:w-auto px-10 py-5 bg-green-600 text-white rounded-2xl font-black text-2xl flex items-center justify-center gap-3 shadow-xl shadow-green-600/30"
            >
              <MessageCircle size={28} fill="currentColor" /> WhatsApp
            </motion.a>
          </div>
        </motion.div>
      </div>

      <div className="grid md:grid-cols-4 gap-12 mb-12 border-b border-slate-900 pb-12">
        <div className="col-span-2">
          <div className="flex items-center gap-2 mb-6">
            <div className="w-8 h-8 bg-blue-600 rounded flex items-center justify-center font-bold">SS</div>
            <span className="text-xl font-bold tracking-tighter">AGENCY</span>
          </div>
          <p className="text-slate-500 max-w-xs mb-6">
            "We Don’t Give Followers. We Give Customers."
          </p>
          <div className="flex gap-4">
            <div className="w-10 h-10 rounded-full bg-slate-900 flex items-center justify-center border border-slate-800 text-slate-400 hover:text-white transition-colors cursor-pointer"><Instagram size={20} /></div>
            <div className="w-10 h-10 rounded-full bg-slate-900 flex items-center justify-center border border-slate-800 text-slate-400 hover:text-white transition-colors cursor-pointer"><Facebook size={20} /></div>
          </div>
        </div>
        <div>
          <h4 className="font-bold mb-6">Links</h4>
          <ul className="space-y-4 text-slate-500">
            <li><a href="#problem" className="hover:text-blue-500">The Problem</a></li>
            <li><a href="#solution" className="hover:text-blue-500">How we work</a></li>
            <li><a href="#services" className="hover:text-blue-500">Services</a></li>
            <li><a href="#founder" className="hover:text-blue-500">Founder</a></li>
          </ul>
        </div>
        <div>
          <h4 className="font-bold mb-6">Contact Us</h4>
          <ul className="space-y-4 text-slate-500">
            <li className="flex gap-2"><Phone size={18} className="text-blue-500" /> 9532792303</li>
            <li className="flex gap-2"><MapPin size={18} className="text-blue-500" /> Serving India (Local Focus)</li>
          </ul>
        </div>
      </div>
      
      <div className="flex flex-col md:flex-row justify-between items-center text-slate-600 text-sm gap-4">
        <p>© 2024 SS Agency. All rights reserved.</p>
        <p>Made with ❤️ for Local Businesses</p>
      </div>
    </div>
  </footer>
);

export default function App() {
  const { scrollYProgress } = useScroll();
  const scaleX = useSpring(scrollYProgress, {
    stiffness: 100,
    damping: 30,
    restDelta: 0.001
  });

  return (
    <div className="min-h-screen bg-slate-950 text-white font-sans selection:bg-blue-500 selection:text-white">
      {/* Progress Bar */}
      <motion.div 
        className="fixed top-0 left-0 right-0 h-1 bg-blue-600 origin-left z-[60]"
        style={{ scaleX }}
      />
      
      <Navbar />
      <Hero />
      <ProblemSection />
      <TransformationSection />
      <StepsSection />
      <ServicesSection />
      <FounderSection />
      <Footer />
      
      {/* Floating CTA for Mobile */}
      <motion.a
        initial={{ y: 100 }}
        animate={{ y: 0 }}
        whileHover={{ scale: 1.1 }}
        href="tel:9532792303"
        className="md:hidden fixed bottom-6 right-6 w-16 h-16 bg-blue-600 rounded-full flex items-center justify-center shadow-2xl z-50 text-white border-2 border-white/20"
      >
        <Phone size={30} fill="currentColor" />
      </motion.a>
    </div>
  );
}
