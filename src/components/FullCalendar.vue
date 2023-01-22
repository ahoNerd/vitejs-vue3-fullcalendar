<script setup>
import { onMounted, ref } from 'vue'
import { Calendar } from '@fullcalendar/core'
import dayGridPlugin from '@fullcalendar/daygrid'
import interactionPlugin from '@fullcalendar/interaction'
import timeGridPlugin from '@fullcalendar/timegrid'
import listPlugin from '@fullcalendar/list'
import resourceTimelinePlugin from '@fullcalendar/resource-timeline'
import resourceTimeGridPlugin from '@fullcalendar/resource-timegrid'
import adaptivePlugin from '@fullcalendar/adaptive'

const calendarEl = ref(null)
const today = new Date()
const dd = String(today.getDate()).padStart(2, '0')
const mm = String(today.getMonth() + 1).padStart(2, '0')
const yyyy = today.getFullYear()
const yesterday = new Date(today)
yesterday.setDate(today.getDate() - 1)
const y_dd = String(yesterday.getDate()).padStart(2, '0')
const y_mm = String(yesterday.getMonth() + 1).padStart(2, '0')
const y_yyyy = yesterday.getFullYear()
const YM = yyyy + '-' + mm
const YESTERDAY = y_yyyy + '-' + y_mm + '-' + y_dd
const TODAY = yyyy + '-' + mm + '-' + dd

const calendarOptions = {
  schedulerLicenseKey: 'CC-Attribution-NonCommercial-NoDerivatives',
  plugins: [
    dayGridPlugin,
    interactionPlugin,
    timeGridPlugin,
    listPlugin,
    resourceTimelinePlugin,
    resourceTimeGridPlugin,
    adaptivePlugin,
  ],
  timeZone: 'UTC',
  initialView: 'dayGridMonth',
  themeSystem: 'bootstrap',
  headerToolbar: {
    left: 'title prev,next',
    center: null,
    right: 'today dayGridMonth,timeGridWeek,timeGridDay,listWeek',
  },
  height: 800,
  contentHeight: 780,
  aspectRatio: 3,
  editable: true,
  droppable: true,
  views: {
    dayGridMonth: {
      dayMaxEventRows: 2,
    },
  },
  direction: 'ltr',
  nowIndicator: true,
  now: TODAY + 'T09:25:00',
  events: [
    {
      id: 'default-event-id-' + Math.floor(Math.random() * 9999999),
      title: 'Reader will be distracted',
      start: YM + '-03T13:30:00',
      className: 'fc-event-danger',
      description:
        "Use a passage of Lorem Ipsum, you need to be sure there isn't anything embarrassing hidden.",
    },
    {
      id: 'default-event-id-' + Math.floor(Math.random() * 9999999),
      title: 'Rabfov va hezow.',
      start: YM + '-14T13:30:00',
      end: YM + '-14',
      className: 'fc-event-success',
      description:
        "Use a passage of Lorem Ipsum, you need to be sure there isn't anything embarrassing hidden.",
    },
    {
      id: 'default-event-id-' + Math.floor(Math.random() * 9999999),
      title: 'The leap into electronic',
      start: YM + '-05',
      end: YM + '-06',
      className: 'fc-event-primary',
      description:
        "Use a passage of Lorem Ipsum, you need to be sure there isn't anything embarrassing hidden.",
    },
    {
      id: 'default-event-id-' + Math.floor(Math.random() * 9999999),
      title: 'Lorem Ipsum passage - Product Release',
      start: YM + '-02',
      end: YM + '-04',
      className: 'fc-event-primary',
      description:
        "Use a passage of Lorem Ipsum, you need to be sure there isn't anything embarrassing hidden.",
    },
    {
      title: 'Gibmuza viib hepobe.',
      start: YM + '-12',
      end: YM + '-10',
      className: 'fc-event-pink-dim',
      description:
        "Use a passage of Lorem Ipsum, you need to be sure there isn't anything embarrassing hidden.",
    },
    {
      id: 'default-event-id-' + Math.floor(Math.random() * 9999999),
      title: 'Jidehse gegoj fupelone.',
      start: YM + '-07T16:00:00',
      className: 'fc-event-danger-dim',
      description:
        "Use a passage of Lorem Ipsum, you need to be sure there isn't anything embarrassing hidden.",
    },
    {
      id: 'default-event-id-' + Math.floor(Math.random() * 9999999),
      title: 'Ke uzipiz zip.',
      start: YM + '-16T16:00:00',
      end: YM + '-14',
      className: 'fc-event-info-dim',
      description:
        "Use a passage of Lorem Ipsum, you need to be sure there isn't anything embarrassing hidden.",
    },
    {
      id: 'default-event-id-' + Math.floor(Math.random() * 9999999),
      title: 'Piece of classical Latin literature',
      start: TODAY,
      end: TODAY + '-01',
      className: 'fc-event-primary',
      description:
        "Use a passage of Lorem Ipsum, you need to be sure there isn't anything embarrassing hidden.",
    },
    {
      id: 'default-event-id-' + Math.floor(Math.random() * 9999999),
      title: 'Nogok kewwib ezidbi.',
      start: TODAY + 'T10:00:00',
      className: 'fc-event-info',
      description:
        "Use a passage of Lorem Ipsum, you need to be sure there isn't anything embarrassing hidden.",
    },
    {
      id: 'default-event-id-' + Math.floor(Math.random() * 9999999),
      title: 'Mifebi ik cumean.',
      start: TODAY + 'T14:30:00',
      className: 'fc-event-warning-dim',
      description:
        "Use a passage of Lorem Ipsum, you need to be sure there isn't anything embarrassing hidden.",
    },
    {
      id: 'default-event-id-' + Math.floor(Math.random() * 9999999),
      title: 'Play Time',
      start: TODAY + 'T17:30:00',
      className: 'fc-event-info',
      description:
        "Use a passage of Lorem Ipsum, you need to be sure there isn't anything embarrassing hidden.",
    },
    {
      id: 'default-event-id-' + Math.floor(Math.random() * 9999999),
      title: 'Rujfogve kabwih haznojuf.',
      start: YESTERDAY + 'T05:00:00',
      className: 'fc-event-danger',
      description:
        "Use a passage of Lorem Ipsum, you need to be sure there isn't anything embarrassing hidden.",
    },
    {
      id: 'default-event-id-' + Math.floor(Math.random() * 9999999),
      title: 'simply dummy text of the printing',
      start: YESTERDAY + 'T07:00:00',
      className: 'fc-event-primary-dim',
      description:
        "Use a passage of Lorem Ipsum, you need to be sure there isn't anything embarrassing hidden.",
    },
  ],
}

onMounted(() => {
  const calendar = new Calendar(calendarEl.value, calendarOptions)
  calendar.render()
})
</script>

<template>
  <div id="calendarEl" ref="calendarEl" />
</template>
