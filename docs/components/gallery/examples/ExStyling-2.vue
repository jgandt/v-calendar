<template>
  <v-calendar
    mode='single'
    :theme-styles='themeStyles'
    :attributes='attributes'
    is-inline>
  </v-calendar>
</template>

<script>
import { getExampleMonthComps } from '@/utils/helpers';

export default {
  data() {
    const { thisMonth, thisMonthYear } = getExampleMonthComps();
    // Show a bar for today's date
    const barDate = new Date();
    // Get start and end dates for the current week
    const start = new Date(thisMonthYear, thisMonth, barDate.getDate() - barDate.getDay());
    const end = new Date(start);
    end.setDate(start.getDate() + 6);
    return {
      selectedDate: null,
      themeStyles: {
        wrapper: {
          color: '#fafafa',
          border: '0',
          padding: '10px',
          background: 'linear-gradient(to bottom right, #6666cc, #0040ff)',
          width: '320px',
        },
        header: {
          padding: '15px 10px 25px 10px',
        },
        headerTitle: {
          fontSize: '1.4rem',
          fontWeight: '300',
        },
        headerArrows: {
          fontSize: '2rem',
          fontWeight: '100',
        },
        headerHorizontalDivider: {
          borderTop: 'solid rgba(255, 255, 255, 0.2) 1px',
          width: '80%',
        },
        weekdays: {
          color: '#2ecdba',
          fontWeight: '600',
          padding: '20px 5px 10px 5px',
        },
      },
      attributes: [
        {
          highlight: {
            backgroundColor: 'rgba(0, 0, 0, 0.2)',
            height: '38px',
          },
          dates: { start, end },
        },
        {
          bar: {
            backgroundColor: '#fafafa',
          },
          dates: barDate,
        },
      ],
    };
  },
};
</script>
