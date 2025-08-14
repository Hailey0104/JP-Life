import React, { useState } from "react";
import { motion } from "framer-motion";
import { CheckCircle2, Globe2, House, CalendarHeart, GraduationCap, ChefHat, Users, Plane, Shield, MessageSquareHeart, MapPin, Phone, Mail, ArrowRight, Star } from "lucide-react";
import { Accordion, AccordionContent, AccordionItem, AccordionTrigger } from "@/components/ui/accordion";
import { Button } from "@/components/ui/button";
import { Card, CardContent, CardDescription, CardFooter, CardHeader, CardTitle } from "@/components/ui/card";
import { Input } from "@/components/ui/input";
import { Textarea } from "@/components/ui/textarea";

// ---------- THEME ----------
const brand = {
  name: "J‑Life",
  tagline: "Live like a local in Japan",
  primary: "from-pink-500 via-rose-500 to-red-500",
};

const FadeIn = ({ children, delay = 0 }) => (
  <motion.div initial={{ opacity: 0, y: 12 }} animate={{ opacity: 1, y: 0 }} transition={{ duration: 0.6, delay }}>
    {children}
  </motion.div>
);

// ---------- NAVBAR ----------
function Navbar() {
  const [open, setOpen] = useState(false);
  const navItems = [
    { label: "Programs", href: "#programs" },
    { label: "How it works", href: "#how" },
    { label: "Host Families", href: "#hosts" },
    { label: "Stories", href: "#stories" },
    { label: "Pricing", href: "#pricing" },
    { label: "FAQ", href: "#faq" },
    { label: "Apply", href: "#apply" },
  ];
  return (
    <header className="sticky top-0 z-50 backdrop-blur supports-[backdrop-filter]:bg-white/70 bg-white/60 border-b">
      <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div className="flex h-16 items-center justify-between">
          <a href="#top" className="flex items-center gap-2">
            <span className="inline-flex h-9 w-9 items-center justify-center rounded-xl bg-gradient-to-br from-rose-500 to-red-500 text-white font-bold">JL</span>
            <div className="leading-tight">
              <div className="font-semibold text-gray-900">{brand.name}</div>
              <div className="text-xs text-gray-500">{brand.tagline}</div>
            </div>
          </a>
          <nav className="hidden md:flex items-center gap-6">
            {navItems.map((i) => (
              <a key={i.href} href={i.href} className="text-gray-700 hover:text-gray-900 text-sm font-medium">
                {i.label}
              </a>
            ))}
            <a href="#apply">
              <Button className="rounded-2xl">Apply now</Button>
            </a>
          </nav>
          <button onClick={() => setOpen(!open)} className="md:hidden p-2 rounded-xl border">☰</button>
        </div>
        {open && (
          <div className="md:hidden py-3 grid gap-3">
            {navItems.map((i) => (
              <a key={i.href} href={i.href} className="block text-gray-700 hover:text-gray-900 text-sm">
                {i.label}
              </a>
            ))}
          </div>
        )}
      </div>
    </header>
  );
}

// ---------- HERO ----------
function Hero() {
  return (
    <section id="top" className="relative overflow-hidden">
      <div className="absolute inset-0 -z-10 bg-gradient-to-br from-rose-50 via-white to-amber-50" />
      <div className="absolute -top-32 -right-32 h-96 w-96 bg-gradient-to-br from-rose-200 to-amber-200 blur-3xl opacity-60 rounded-full" />
      <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-20 md:py-28">
        <div className="grid md:grid-cols-2 gap-10 items-center">
          <FadeIn>
            <h1 className="text-4xl md:text-6xl font-extrabold tracking-tight text-gray-900">
              Experience real Japanese life —
              <span className="block bg-clip-text text-transparent bg-gradient-to-r from-rose-600 to-red-500"> from tatami to table.</span>
            </h1>
          </FadeIn>
          <FadeIn delay={0.1}>
            <p className="text-lg text-gray-600 mt-4 md:mt-2">
              {brand.name} connects students worldwide with carefully vetted Japanese host families. Live the language, join everyday routines, and build friendships that last a lifetime.
            </p>
            <div className="mt-6 flex gap-3">
              <a href="#apply"><Button size="lg" className="rounded-2xl">Start your application</Button></a>
              <a href="#programs"><Button size="lg" variant="outline" className="rounded-2xl">Explore programs</Button></a>
            </div>
            <div className="mt-6 flex items-center gap-3 text-sm text-gray-500">
              <Shield className="h-4 w-4" />
              <span>24/7 student support • Government-compliant safeguarding • 1k+ alumni</span>
            </div>
          </FadeIn>
          <FadeIn delay={0.15}>
            <div className="relative">
              <img
                src="https://images.unsplash.com/photo-1549692520-acc6669e2f0c?q=80&w=1400&auto=format&fit=crop"
                alt="Japanese street with lanterns"
                className="rounded-3xl shadow-2xl border"
              />
              <div className="absolute -bottom-6 -left-6 bg-white shadow-xl rounded-2xl p-4 flex items-center gap-3">
                <House className="h-6 w-6 text-rose-600" />
                <div>
                  <div className="font-semibold">Verified Hosts</div>
                  <div className="text-xs text-gray-500">Across Tokyo, Kansai, Hokkaido & more</div>
                </div>
              </div>
            </div>
          </FadeIn>
        </div>
      </div>
    </section>
  );
}

// ---------- HOW IT WORKS ----------
function HowItWorks() {
  const steps = [
    { icon: Globe2, title: "Tell us about you", desc: "Share goals, dates, Japanese level and dietary needs." },
    { icon: Users, title: "Match & meet", desc: "We hand‑match a host family; meet them on a video call." },
    { icon: Shield, title: "Prepare & protect", desc: "Pre‑departure orientation, insurance guidance, safety briefings." },
    { icon: House, title: "Live like a local", desc: "Cook, commute, celebrate and explore together." },
  ];
  return (
    <section id="how" className="py-20">
      <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <FadeIn>
          <h2 className="text-3xl md:text-4xl font-bold text-gray-900 mb-10">How it works</h2>
        </FadeIn>
        <div className="grid md:grid-cols-4 gap-6">
          {steps.map((s, idx) => (
            <FadeIn key={s.title} delay={idx * 0.05}>
              <Card className="rounded-3xl">
                <CardHeader>
                  <div className="h-12 w-12 rounded-2xl bg-rose-50 flex items-center justify-center">
                    <s.icon className="h-6 w-6 text-rose-600" />
                  </div>
                  <CardTitle className="mt-3 text-xl">{s.title}</CardTitle>
                </CardHeader>
                <CardContent>
                  <p className="text-gray-600">{s.desc}</p>
                </CardContent>
              </Card>
            </FadeIn>
          ))}
        </div>
      </div>
    </section>
  );
}

// ---------- PROGRAMS ----------
function Programs() {
  const products = [
    {
      icon: CalendarHeart,
      title: "Weekend Micro‑Immersions",
      desc: "2–5 days with a host family — perfect add‑on to your Japan trip.",
      perks: ["Breakfast & dinner", "Local day trip", "Orientation call"],
      img: "https://images.unsplash.com/photo-1549693578-d683be217e58?q=80&w=1400&auto=format&fit=crop",
    },
    {
      icon: GraduationCap,
      title: "Semester Homestay + School",
      desc: "Attend a local high school or language school while living with your hosts.",
      perks: ["Placement assistance", "Transit pass setup", "Monthly check‑ins"],
      img: "https://images.unsplash.com/photo-1529156069898-49953e39b3ac?q=80&w=1400&auto=format&fit=crop",
    },
    {
      icon: ChefHat,
      title: "Language + Home Cooking",
      desc: "Daily conversation practice and hands‑on Japanese cooking sessions.",
      perks: ["JLPT‑aligned study plan", "3 cooking classes/week", "Cultural workshops"],
      img: "https://images.unsplash.com/photo-1532634896-26909d0d4b6a?q=80&w=1400&auto=format&fit=crop",
    },
    {
      icon: Plane,
      title: "Rural Farmstay",
      desc: "Unplug in Hokkaido or Kyushu—help with harvests, learn sustainable living.",
      perks: ["Seasonal activities", "Nature hikes", "Community festivals"],
      img: "https://images.unsplash.com/photo-1480796927426-f609979314bd?q=80&w=1400&auto=format&fit=crop",
    },
  ];
  return (
    <section id="programs" className="py-20 bg-gradient-to-b from-white to-rose-50/60">
      <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <FadeIn>
          <h2 className="text-3xl md:text-4xl font-bold text-gray-900 mb-3">Programs designed for real life</h2>
          <p className="text-gray-600 mb-10">Choose the vibe that fits you — city lights, school life, or countryside calm.</p>
        </FadeIn>
        <div className="grid md:grid-cols-2 gap-6">
          {products.map((p, idx) => (
            <FadeIn key={p.title} delay={idx * 0.07}>
              <Card className="overflow-hidden rounded-3xl">
                <div className="grid md:grid-cols-2">
                  <img src={p.img} alt={p.title} className="h-64 md:h-full w-full object-cover" />
                  <div>
                    <CardHeader className="space-y-2">
                      <div className="h-12 w-12 rounded-2xl bg-rose-50 flex items-center justify-center"><p.icon className="h-6 w-6 text-rose-600"/></div>
                      <CardTitle>{p.title}</CardTitle>
                      <CardDescription className="text-gray-600">{p.desc}</CardDescription>
                    </CardHeader>
                    <CardContent>
                      <ul className="space-y-2">
                        {p.perks.map((perk) => (
                          <li key={perk} className="flex items-center gap-2 text-gray-700"><CheckCircle2 className="h-4 w-4 text-emerald-600" /> {perk}</li>
                        ))}
                      </ul>
                    </CardContent>
                    <CardFooter>
                      <a href="#apply"><Button className="rounded-2xl">Apply for {p.title}</Button></a>
                    </CardFooter>
                  </div>
                </div>
              </Card>
            </FadeIn>
          ))}
        </div>
      </div>
    </section>
  );
}

// ---------- HOST FAMILIES ----------
function Hosts() {
  const features = [
    { icon: House, title: "Vetted Homes", desc: "ID checks, interviews, and home visits for safety and comfort." },
    { icon: MessageSquareHeart, title: "Cultural Exchange", desc: "Daily routines: cooking, cleaning day, shopping, matsuri, seasonal customs." },
    { icon: MapPin, title: "Diverse Regions", desc: "Tokyo & Kansai hubs plus rural prefectures for slower living." },
  ];
  return (
    <section id="hosts" className="py-20">
      <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <FadeIn>
          <h2 className="text-3xl md:text-4xl font-bold text-gray-900 mb-3">Host families you can trust</h2>
          <p className="text-gray-600 mb-10">We accept fewer than 30% of applicants to keep standards high.</p>
        </FadeIn>
        <div className="grid md:grid-cols-3 gap-6">
          {features.map((f, idx) => (
            <FadeIn key={f.title} delay={idx * 0.06}>
              <Card className="rounded-3xl">
                <CardHeader>
                  <div className="h-12 w-12 rounded-2xl bg-rose-50 flex items-center justify-center"><f.icon className="h-6 w-6 text-rose-600"/></div>
                  <CardTitle>{f.title}</CardTitle>
                </CardHeader>
                <CardContent>
                  <p className="text-gray-600">{f.desc}</p>
                </CardContent>
              </Card>
            </FadeIn>
          ))}
        </div>
      </div>
    </section>
  );
}

// ---------- STORIES ----------
function Stories() {
  const items = [
    {
      name: "Aria, Australia",
      quote: "My host grandma taught me miso soup from scratch — we spoke only Japanese in the kitchen and my listening skyrocketed!",
      img: "https://images.unsplash.com/photo-1544005313-94ddf0286df2?q=80&w=800&auto=format&fit=crop",
    },
    {
      name: "Diego, Mexico",
      quote: "Commuting to language school with my host brother made Tokyo feel like home by week two.",
      img: "https://images.unsplash.com/photo-1547425260-76bcadfb4f2c?q=80&w=800&auto=format&fit=crop",
    },
    {
      name: "Linh, Vietnam",
      quote: "The Obon festival in a small town was the highlight — I danced Bon Odori with the neighbors!",
      img: "https://images.unsplash.com/photo-1541532713592-79a0317b6b77?q=80&w=800&auto=format&fit=crop",
    },
  ];
  return (
    <section id="stories" className="py-20 bg-white">
      <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <FadeIn>
          <h2 className="text-3xl md:text-4xl font-bold text-gray-900 mb-3">Student stories</h2>
          <p className="text-gray-600 mb-10">Every home is different. That’s the magic.</p>
        </FadeIn>
        <div className="grid md:grid-cols-3 gap-6">
          {items.map((t, i) => (
            <FadeIn key={t.name} delay={i * 0.06}>
              <Card className="rounded-3xl overflow-hidden">
                <img src={t.img} alt={t.name} className="h-56 w-full object-cover" />
                <CardContent className="pt-6">
                  <div className="flex items-center gap-2 text-amber-500 mb-2">
                    {Array.from({ length: 5 }).map((_, idx) => <Star key={idx} className="h-4 w-4 fill-current" />)}
                  </div>
                  <blockquote className="text-gray-700">“{t.quote}”</blockquote>
                </CardContent>
                <CardFooter className="text-sm text-gray-500">— {t.name}</CardFooter>
              </Card>
            </FadeIn>
          ))}
        </div>
      </div>
    </section>
  );
}

// ---------- PRICING ----------
function Pricing() {
  const tiers = [
    {
      name: "Micro‑Immersion",
      price: "¥68,000",
      period: "/ 3–5 days",
      features: ["2 meals/day", "Airport welcome option", "Mini cultural workshop"],
      badge: "Popular",
    },
    {
      name: "Semester Homestay",
      price: "¥420,000",
      period: "/ per term",
      features: ["Placement support", "Monthly check‑ins", "Guardianship available"],
      badge: "Best value",
    },
    {
      name: "Rural Farmstay",
      price: "¥120,000",
      period: "/ week",
      features: ["Seasonal activities", "Community guide", "Insurance guidance"],
    },
  ];
  return (
    <section id="pricing" className="py-20 bg-gradient-to-t from-white to-rose-50/60">
      <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <FadeIn>
          <h2 className="text-3xl md:text-4xl font-bold text-gray-900 mb-3">Transparent pricing</h2>
          <p className="text-gray-600 mb-10">Scholarships and payment plans are available. Prices shown are examples and may vary by season and region.</p>
        </FadeIn>
        <div className="grid md:grid-cols-3 gap-6">
          {tiers.map((t, i) => (
            <FadeIn key={t.name} delay={i * 0.05}>
              <Card className="rounded-3xl">
                <CardHeader>
                  {t.badge && <span className="inline-flex items-center px-2 py-1 rounded-full text-xs bg-rose-100 text-rose-700 w-fit">{t.badge}</span>}
                  <CardTitle className="mt-2">{t.name}</CardTitle>
                  <CardDescription>
                    <span className="text-3xl font-bold text-gray-900">{t.price}</span>
                    <span className="text-gray-500"> {t.period}</span>
                  </CardDescription>
                </CardHeader>
                <CardContent>
                  <ul className="space-y-2">
                    {t.features.map((f) => (
                      <li key={f} className="flex items-center gap-2 text-gray-700"><CheckCircle2 className="h-4 w-4 text-emerald-600"/> {f}</li>
                    ))}
                  </ul>
                </CardContent>
                <CardFooter>
                  <a href="#apply"><Button className="w-full rounded-2xl">Apply</Button></a>
                </CardFooter>
              </Card>
            </FadeIn>
          ))}
        </div>
      </div>
    </section>
  );
}

// ---------- FAQ ----------
function FAQ() {
  const qs = [
    { q: "Who can apply?", a: "High‑school and university students aged 15+ are welcome. Under‑18s require parental consent." },
    { q: "Do I need Japanese?", a: "No, but a little goes a long way. We offer prep classes and a JLPT‑aligned study path." },
    { q: "What about safety?", a: "Every host is vetted. Our staff are on call 24/7, and we check‑in weekly during your first month." },
    { q: "Can I choose my city?", a: "Tell us your preference — Tokyo, Osaka, Kyoto, Sapporo and more. We’ll match you thoughtfully." },
  ];
  return (
    <section id="faq" className="py-20">
      <div className="max-w-3xl mx-auto px-4 sm:px-6 lg:px-8">
        <FadeIn>
          <h2 className="text-3xl md:text-4xl font-bold text-gray-900 mb-6 text-center">Frequently asked questions</h2>
        </FadeIn>
        <Accordion type="single" collapsible className="rounded-3xl border">
          {qs.map((item, i) => (
            <AccordionItem key={i} value={`item-${i}`}>
              <AccordionTrigger className="px-4">{item.q}</AccordionTrigger>
              <AccordionContent className="px-4 text-gray-600">{item.a}</AccordionContent>
            </AccordionItem>
          ))}
        </Accordion>
      </div>
    </section>
  );
}

// ---------- APPLY FORM ----------
function ApplyForm() {
  const [form, setForm] = useState({ name: "", email: "", nationality: "", program: "", dates: "", message: "" });
  const [submitted, setSubmitted] = useState(false);
  function update(k, v) { setForm({ ...form, [k]: v }); }
  function submit(e) {
    e.preventDefault();
    // Demo only. In production, POST to your backend/API.
    setSubmitted(true);
  }
  return (
    <section id="apply" className="py-20 bg-white">
      <div className="max-w-4xl mx-auto px-4 sm:px-6 lg:px-8">
        <FadeIn>
          <h2 className="text-3xl md:text-4xl font-bold text-gray-900 mb-3 text-center">Start your J‑Life journey</h2>
          <p className="text-gray-600 mb-8 text-center">Tell us a little about you and your ideal experience. We’ll reply within two business days.</p>
        </FadeIn>
        <Card className="rounded-3xl">
          <form onSubmit={submit} className="grid gap-6 p-6">
            <div className="grid md:grid-cols-2 gap-4">
              <div>
                <label className="text-sm font-medium">Full name</label>
                <Input required value={form.name} onChange={(e) => update("name", e.target.value)} placeholder="Your name" />
              </div>
              <div>
                <label className="text-sm font-medium">Email</label>
                <Input type="email" required value={form.email} onChange={(e) => update("email", e.target.value)} placeholder="you@example.com" />
              </div>
              <div>
                <label className="text-sm font-medium">Nationality</label>
                <Input value={form.nationality} onChange={(e) => update("nationality", e.target.value)} placeholder="e.g., Australian" />
              </div>
              <div>
                <label className="text-sm font-medium">Preferred program</label>
                <select className="w-full h-10 rounded-md border px-3" value={form.program} onChange={(e) => update("program", e.target.value)}>
                  <option value="">Select a program…</option>
                  <option>Weekend Micro‑Immersion</option>
                  <option>Semester Homestay + School</option>
                  <option>Language + Home Cooking</option>
                  <option>Rural Farmstay</option>
                </select>
              </div>
              <div className="md:col-span-2">
                <label className="text-sm font-medium">Dates / timing</label>
                <Input value={form.dates} onChange={(e) => update("dates", e.target.value)} placeholder="e.g., Jan–Mar 2026 or 5–10 Oct 2025" />
              </div>
              <div className="md:col-span-2">
                <label className="text-sm font-medium">Tell us more</label>
                <Textarea rows={5} value={form.message} onChange={(e) => update("message", e.target.value)} placeholder="Goals, Japanese level, allergies/diet, city preference…" />
              </div>
            </div>
            {!submitted ? (
              <Button type="submit" size="lg" className="rounded-2xl w-full">Submit application</Button>
            ) : (
              <div className="p-4 rounded-2xl bg-emerald-50 text-emerald-700 text-center font-medium">
                Thanks! Your details are captured locally for demo. Connect this form to your backend to receive submissions.
              </div>
            )}
          </form>
        </Card>
        <div className="mt-8 flex items-center justify-center gap-6 text-gray-600">
          <div className="flex items-center gap-2"><Phone className="h-4 w-4"/> +81 3 1234 5678</div>
          <div className="flex items-center gap-2"><Mail className="h-4 w-4"/> hello@jlife.jp</div>
        </div>
      </div>
    </section>
  );
}

// ---------- FOOTER ----------
function Footer() {
  return (
    <footer className="py-12 border-t bg-white">
      <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div className="grid md:grid-cols-4 gap-8">
          <div>
            <div className="flex items-center gap-2">
              <span className="inline-flex h-9 w-9 items-center justify-center rounded-xl bg-gradient-to-br from-rose-500 to-red-500 text-white font-bold">JL</span>
              <span className="font-semibold">{brand.name}</span>
            </div>
            <p className="mt-3 text-sm text-gray-600">{brand.tagline}. Homestays across Japan with caring, verified hosts.</p>
          </div>
          <div>
            <div className="font-semibold mb-3">Explore</div>
            <ul className="space-y-2 text-sm text-gray-600">
              <li><a href="#programs">Programs</a></li>
              <li><a href="#hosts">Host Families</a></li>
              <li><a href="#stories">Stories</a></li>
              <li><a href="#pricing">Pricing</a></li>
            </ul>
          </div>
          <div>
            <div className="font-semibold mb-3">Help</div>
            <ul className="space-y-2 text-sm text-gray-600">
              <li><a href="#faq">FAQs</a></li>
              <li>Student handbook (PDF)</li>
              <li>Safeguarding policy</li>
            </ul>
          </div>
          <div>
            <div className="font-semibold mb-3">Contact</div>
            <ul className="space-y-2 text-sm text-gray-600">
              <li className="flex items-center gap-2"><MapPin className="h-4 w-4"/> Tokyo • Osaka • Sapporo</li>
              <li className="flex items-center gap-2"><Phone className="h-4 w-4"/> +81 3 1234 5678</li>
              <li className="flex items-center gap-2"><Mail className="h-4 w-4"/> hello@jlife.jp</li>
            </ul>
          </div>
        </div>
        <div className="mt-8 text-xs text-gray-500">© {new Date().getFullYear()} {brand.name}. All rights reserved.</div>
      </div>
    </footer>
  );
}

// ---------- PAGE ----------
export default function JLifeWebsite() {
  return (
    <div className="font-sans text-gray-900">
      <Navbar />
      <Hero />
      <HowItWorks />
      <Programs />
      <Hosts />
      <Stories />
      <Pricing />
      <FAQ />
      <ApplyForm />
      <Footer />

      {/* CTA ribbon */}
      <div className="fixed bottom-4 inset-x-4 md:inset-x-auto md:right-6 md:bottom-6">
        <div className="bg-gradient-to-r from-rose-500 to-red-500 text-white rounded-2xl shadow-2xl flex items-center justify-between px-4 py-3 gap-3">
          <div className="flex items-center gap-3 text-sm md:text-base">
            <CalendarHeart className="h-5 w-5" />
            <span>2026 Spring placements open now • Limited rural spots</span>
          </div>
          <a href="#apply" className="inline-flex items-center gap-2 text-sm font-medium">
            Apply now <ArrowRight className="h-4 w-4" />
          </a>
        </div>
      </div>
    </div>
  );
}
