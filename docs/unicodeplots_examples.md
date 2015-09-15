### Lines

A simple line plot of the 3 columns.

```julia
plot(rand(100,3))
```

![](../img/unicodeplots/unicodeplots_example_1.png)

### Functions

Plot multiple functions.

```julia
plot(0:0.01:4π,[sin,cos])
```

![](../img/unicodeplots/unicodeplots_example_2.png)

### 

You can also call it with plot(f, xmin, xmax).

```julia
plot([sin,cos],0,4π)
```

![](../img/unicodeplots/unicodeplots_example_3.png)

### 

Or make a parametric plot with plot(fx, fy, umin, umax).

```julia
plot(sin,(x->begin  # /Users/tom/.julia/v0.4/Plots/docs/example_generation.jl, line 33:
            sin(2x)
        end),0,2π)
```

![](../img/unicodeplots/unicodeplots_example_4.png)

### Global

Change the guides/background without a separate call.

```julia
plot(rand(10); title="TITLE",xlabel="XLABEL",ylabel="YLABEL",background_color=RGB(0.5,0.5,0.5))
```

![](../img/unicodeplots/unicodeplots_example_5.png)

### Two-axis

Use the `axis` or `axiss` arguments.

Note: This is only supported with Qwt right now

```julia
plot(Vector[randn(100),randn(100) * 100]; axiss=[:left,:right],ylabel="LEFT",yrightlabel="RIGHT")
```

![](../img/unicodeplots/unicodeplots_example_6.png)

### Vectors w/ pluralized args

Plot multiple series with different numbers of points.  Mix arguments that apply to all series (singular... see `marker`) with arguments unique to each series (pluralized... see `colors`).

```julia
plot(Vector[rand(10),rand(20)]; marker=:ellipse,markersize=8,colors=[:red,:blue])
```

![](../img/unicodeplots/unicodeplots_example_7.png)

### Build plot in pieces

Start with a base plot...

```julia
plot(rand(100) / 3; reg=true,fillto=0)
```

![](../img/unicodeplots/unicodeplots_example_8.png)

### 

and add to it later.

```julia
scatter!(rand(100); markersize=6,color=:blue)
```

![](../img/unicodeplots/unicodeplots_example_9.png)

### Lots of line types

Options: (:line, :step, :stepinverted, :sticks, :dots, :none, :heatmap, :hexbin, :hist, :bar)  
Note: some may not work with all backends

```julia
plot(rand(20,4); linetypes=[:line,:step,:sticks,:dots],labels=["line","step","sticks","dots"])
```

![](../img/unicodeplots/unicodeplots_example_11.png)

### Lots of line styles

Options: (:solid, :dash, :dot, :dashdot, :dashdotdot)  
Note: some may not work with all backends

```julia
plot(rand(20,5); linestyles=[:solid,:dash,:dot,:dashdot,:dashdotdot],labels=["solid","dash","dot","dashdot","dashdotdot"])
```

![](../img/unicodeplots/unicodeplots_example_12.png)

### Lots of marker types

Options: (:none, :ellipse, :rect, :diamond, :utriangle, :dtriangle, :cross, :xcross, :star1, :star2, :hexagon)  
Note: some may not work with all backends

```julia
plot(repmat(collect(1:10)',10,1); markers=[:ellipse,:rect,:diamond,:utriangle,:dtriangle,:cross,:xcross,:star1,:star2,:hexagon],labels=["ellipse","rect","diamond","utriangle","dtriangle","cross","xcross","star1","star2","hexagon"],linetype=:none,markersize=10)
```

![](../img/unicodeplots/unicodeplots_example_13.png)

### Bar

x is the midpoint of the bar. (todo: allow passing of edges instead of midpoints)

```julia
bar(randn(1000))
```

![](../img/unicodeplots/unicodeplots_example_14.png)

### Histogram

note: fillto isn't supported on all backends

```julia
histogram(randn(1000); nbins=50,fillto=20)
```

![](../img/unicodeplots/unicodeplots_example_15.png)

### Subplots

  subplot and subplot! are distinct commands which create many plots and add series to them in a circular fashion.
  You can define the layout with keyword params... either set the number of plots `n` (and optionally number of rows `nr` or 
  number of columns `nc`), or you can set the layout directly with `layout`.  

  Note: Gadfly is not very friendly here, and although you can create a plot and save a PNG, I haven't been able to actually display it.


```julia
subplot(randn(100,5); layout=[1,1,3],linetypes=[:line,:hist,:dots,:step,:bar],nbins=10,legend=false)
```

![](../img/unicodeplots/unicodeplots_example_16.png)

### Adding to subplots

Note here the automatic grid layout, as well as the order in which new series are added to the plots.

```julia
subplot(randn(100,5); n=4)
```

![](../img/unicodeplots/unicodeplots_example_17.png)

### 



```julia
subplot!(randn(100,3))
```

![](../img/unicodeplots/unicodeplots_example_18.png)
