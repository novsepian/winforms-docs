---
title: Watterfall
page_title: Watterfall
description: Watterfall
slug: charview-series-types-waterfall
tags: watterfall
published: True
position: 16
---

# Watterfall



## 

A __Waterfall__ chart type (a.k.a., flying bricks, bridge, etc.) shows the cumulative effect of positive or negative
          values on the starting point.
          Its purpose is to provide a better understanding of how an initial amount is influenced by subsequently added positive or negative values. 
          Generally, the first and last items of a Waterfall series are denoted by whole columns while items in the middle are shown as floating columns. 
          You can, however, control whether the last and middle items display the current value (e.g., a floating column set through the Value property) 
          or the sum of all previous values (e.g., a whole column using the __IsSummary__ and __IsTotal__
          properties of the __WaterfallDataPoint__).
          A Waterfall chart is useful for different types of quantitative analysis related to inventory, cash flows, performance, etc.
          This chart type looks like a Range Column chart where the low or high value of a subsequent item is connected to the preceding one with a line.
        ![charview-series-types-waterfall 001](images/charview-series-types-waterfall001.png)

The example above can be achieve with the following code snippet: 
        

#### __[C#] __

{{region UnboundMode}}
	            WaterfallSeries series = new WaterfallSeries();
	            series.DataPoints.Add(new WaterfallDataPoint(50000, false, false, "Beginning\nBalance"));
	            series.DataPoints.Add(new WaterfallDataPoint(17000, false, false, "Jan"));
	            series.DataPoints.Add(new WaterfallDataPoint(14000, false, false, "Feb"));
	            series.DataPoints.Add(new WaterfallDataPoint(-12000, false, false, "Mar"));
	            series.DataPoints.Add(new WaterfallDataPoint(69000, true, false, "Q1"));
	            series.DataPoints.Add(new WaterfallDataPoint(-22000, false, false, "Apr"));
	            series.DataPoints.Add(new WaterfallDataPoint(-18000, false, false, "May"));
	            series.DataPoints.Add(new WaterfallDataPoint(10000, false, false, "Jun"));
	            series.DataPoints.Add(new WaterfallDataPoint(-30000, true, false, "Q2"));
	            series.DataPoints.Add(new WaterfallDataPoint(39000, false, true, "Ending\nBalance"));
	            this.radChartView1.Series.Add(series);
	{{endregion}}



#### __[VB.NET] __

{{region UnboundMode}}
	        Dim series As New WaterfallSeries()
	        series.DataPoints.Add(New WaterfallDataPoint(50000, False, False, "Beginning" & vbLf & "Balance"))
	        series.DataPoints.Add(New WaterfallDataPoint(17000, False, False, "Jan"))
	        series.DataPoints.Add(New WaterfallDataPoint(14000, False, False, "Feb"))
	        series.DataPoints.Add(New WaterfallDataPoint(-12000, False, False, "Mar"))
	        series.DataPoints.Add(New WaterfallDataPoint(69000, True, False, "Q1"))
	        series.DataPoints.Add(New WaterfallDataPoint(-22000, False, False, "Apr"))
	        series.DataPoints.Add(New WaterfallDataPoint(-18000, False, False, "May"))
	        series.DataPoints.Add(New WaterfallDataPoint(10000, False, False, "Jun"))
	        series.DataPoints.Add(New WaterfallDataPoint(-30000, True, False, "Q2"))
	        series.DataPoints.Add(New WaterfallDataPoint(39000, False, True, "Ending" & vbLf & "Balance"))
	        Me.radChartView1.Series.Add(series)
	        '#End Region
	    End Sub
	End Class



To achieve the same chart in a data bound mode you will need appropriate data. Here is an example:
        

#### __[C#] __

{{region DataBinding}}
	            DataTable table = new DataTable();
	
	            table.Columns.Add("Category", typeof(string));
	            table.Columns.Add("Value", typeof(double));
	            table.Columns.Add("Summary", typeof(bool));
	            table.Columns.Add("Total", typeof(bool));
	
	            table.Rows.Add("Beginning\nBalance", 50000, false, false);
	            table.Rows.Add("Jan", 17000, false, false);
	            table.Rows.Add("Feb", 14000, false, false);
	            table.Rows.Add("Mar", -12000, false, false);
	            table.Rows.Add("Q1", 69000, true, false);
	            table.Rows.Add("Apr", -22000, false, false);
	            table.Rows.Add("May", -18000, false, false);
	            table.Rows.Add("Jun", 10000, false, false);
	            table.Rows.Add("Q2", -30000, true, false);
	            table.Rows.Add("Ending\nBalance", 39000, false, true);
	
	            WaterfallSeries series = new WaterfallSeries();
	            series.ValueMember = "Value";
	            series.CategoryMember = "Category";
	            series.SummaryMember = "Summary";
	            series.TotalMember = "Total";
	            series.DataSource = table;
	
	            this.radChartView1.Series.Add(series);
	{{endregion}}



#### __[VB.NET] __

{{region DataBinding}}
	        Dim table As New DataTable()
	
	        table.Columns.Add("Category", GetType(String))
	        table.Columns.Add("Value", GetType(Double))
	        table.Columns.Add("Summary", GetType(Boolean))
	        table.Columns.Add("Total", GetType(Boolean))
	
	        table.Rows.Add("Beginning" & vbLf & "Balance", 50000, False, False)
	        table.Rows.Add("Jan", 17000, False, False)
	        table.Rows.Add("Feb", 14000, False, False)
	        table.Rows.Add("Mar", -12000, False, False)
	        table.Rows.Add("Q1", 69000, True, False)
	        table.Rows.Add("Apr", -22000, False, False)
	        table.Rows.Add("May", -18000, False, False)
	        table.Rows.Add("Jun", 10000, False, False)
	        table.Rows.Add("Q2", -30000, True, False)
	        table.Rows.Add("Ending" & vbLf & "Balance", 39000, False, True)
	
	        Dim series As New WaterfallSeries()
	        series.ValueMember = "Value"
	        series.CategoryMember = "Category"
	        series.SummaryMember = "Summary"
	        series.TotalMember = "Total"
	        series.DataSource = table
	
	        Me.radChartView1.Series.Add(series)
	        '#End Region
	    End Sub
	
	    Private Sub UnboundMode()
	        '#Region "UnboundMode"
	        Dim series As New WaterfallSeries()
	        series.DataPoints.Add(New WaterfallDataPoint(50000, False, False, "Beginning" & vbLf & "Balance"))
	        series.DataPoints.Add(New WaterfallDataPoint(17000, False, False, "Jan"))
	        series.DataPoints.Add(New WaterfallDataPoint(14000, False, False, "Feb"))
	        series.DataPoints.Add(New WaterfallDataPoint(-12000, False, False, "Mar"))
	        series.DataPoints.Add(New WaterfallDataPoint(69000, True, False, "Q1"))
	        series.DataPoints.Add(New WaterfallDataPoint(-22000, False, False, "Apr"))
	        series.DataPoints.Add(New WaterfallDataPoint(-18000, False, False, "May"))
	        series.DataPoints.Add(New WaterfallDataPoint(10000, False, False, "Jun"))
	        series.DataPoints.Add(New WaterfallDataPoint(-30000, True, False, "Q2"))
	        series.DataPoints.Add(New WaterfallDataPoint(39000, False, True, "Ending" & vbLf & "Balance"))
	        Me.radChartView1.Series.Add(series)
	        '#End Region
	    End Sub
	End Class

