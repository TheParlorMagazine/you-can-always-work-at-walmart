import { useState } from 'react'
import { Card, CardContent } from '@/components/ui/card'
import { Button } from '@/components/ui/button'
import { ExternalLink, ChevronLeft, ChevronRight } from 'lucide-react'
import { AnimatePresence, motion } from 'framer-motion'

type Metric = {
  title: string
  value: string
  unit: string
  category: string
  source: string
  link: string
}

const metrics: Metric[] = [
  {
    title: 'Retail job hours reduction with automation (range)',
    value: '55–65%',
    unit: 'percent',
    category: 'Automation impact (Retail)',
    source: 'McKinsey & Company — Automation in retail: an executive overview for getting ready (2019)',
    link: 'https://www.mckinsey.com/industries/retail/our-insights/automation-in-retail-an-executive-overview-for-getting-ready'
  },
  {
    title: 'McDonald’s global workforce reduction since 2012',
    value: '34%',
    unit: 'percent',
    category: 'Labor trend (QSR)',
    source: "Statista — Number of employees at McDonald's Corporation worldwide from 2005 to 2023",
    link: 'https://www.statista.com/statistics/819966/mcdonald-s-number-of-employees/'
  },
  {
    title: 'Tech industry layoffs since 2022',
    value: '530,000',
    unit: 'people',
    category: 'Labor trend (Tech)',
    source: 'YouTube (cited) — Tech layoff compilation / analysis',
    link: 'http://youtube.com/watch?v=mlYPJ8yFk9I&t=75'
  },
  {
    title: 'Tech industry layoffs in 2023',
    value: '200,000',
    unit: 'people',
    category: 'Labor trend (Tech)',
    source: 'YouTube (cited) — Tech layoff compilation / analysis',
    link: 'http://youtube.com/watch?v=mlYPJ8yFk9I&t=75'
  },
  {
    title: 'U.S. CEOs anticipating workforce reductions (next 6–12 months)',
    value: '30%',
    unit: 'percent',
    category: 'Executive outlook (HR)',
    source: 'HR Dive — CEOs expect to reduce workforce during next 12 months',
    link: 'https://www.hrdive.com/news/ceos-expect-to-reduce-workforce-during-next-12-months/757611/'
  },
  {
    title: 'Amazon robot-to-human employment relationship',
    value: 'Reported as "more robots than people"',
    unit: '—',
    category: 'Automation (Logistics)',
    source: 'New York Post — Amazon will soon employ more robots than humans: report',
    link: 'https://nypost.com/2025/07/02/business/amazon-will-soon-employ-more-robots-than-humans-report/'
  }
]

const variants = {
  enter: (direction: number) => ({
    x: direction > 0 ? 80 : -80,
    opacity: 0,
    position: 'absolute' as const
  }),
  center: {
    x: 0,
    opacity: 1,
    position: 'static' as const
  },
  exit: (direction: number) => ({
    x: direction > 0 ? -80 : 80,
    opacity: 0,
    position: 'absolute' as const
  })
}

export default function AutomationMetricsCarousel() {
  const [index, setIndex] = useState(0)
  const [direction, setDirection] = useState(0)

  const paginate = (dir: number) => {
    setDirection(dir)
    setIndex((prev) => (prev + dir + metrics.length) % metrics.length)
  }

  const current = metrics[index]

  return (
    <div className="flex flex-col items-center w-full max-w-xl mx-auto">
      <div className="relative w-full">
        <Card className="w-full p-6 bg-white shadow-md overflow-hidden">
          <div className="flex items-center justify-between mb-4">
            <Button variant="outline" size="icon" onClick={() => paginate(-1)} aria-label="Previous">
              <ChevronLeft className="h-5 w-5" />
            </Button>
            <p className="text-sm text-gray-500">{index + 1} / {metrics.length}</p>
            <Button variant="outline" size="icon" onClick={() => paginate(1)} aria-label="Next">
              <ChevronRight className="h-5 w-5" />
            </Button>
          </div>

          <div className="relative min-h-[220px]">
            <AnimatePresence custom={direction} mode="popLayout" initial={false}>
              <motion.div
                key={index}
                custom={direction}
                variants={variants}
                initial="enter"
                animate="center"
                exit="exit"
                transition={{ duration: 0.28, ease: 'easeInOut' }}
                className="text-center"
              >
                <h2 className="text-lg font-semibold mb-3">{current.title}</h2>
                <CardContent className="space-y-3">
                  <div className="text-4xl font-bold text-blue-600">{current.value}</div>
                  <p className="text-sm text-gray-600">Unit: {current.unit}</p>
                  <p className="text-sm text-gray-600">Category: {current.category}</p>
                  <a
                    href={current.link}
                    target="_blank"
                    rel="noopener noreferrer"
                    className="inline-flex items-center text-blue-600 hover:underline"
                  >
                    <ExternalLink className="h-4 w-4 mr-1" /> View Source
                  </a>
                  <p className="text-xs text-gray-500 mt-1">{current.source}</p>
                </CardContent>
              </motion.div>
            </AnimatePresence>
          </div>
        </Card>
      </div>

      <div className="mt-2 text-xs text-gray-500">
        Tip: Use the arrow buttons to slide through metrics.
      </div>
    </div>
  )
}
