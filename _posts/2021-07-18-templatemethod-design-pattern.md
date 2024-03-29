---
layout: post
title: "Template Method Design Pattern"
name: "2021-07-18-templatemethod-design-pattern"
description: "Simple example of template method design pattern."
tags: "c#,.net,.net core,template method pattern,code,design patterns,UML,unified modeling language,technical article,blog,post"
date: 2021-07-18
---

<p>Builder design pattern is a most often used software design pattern. Please refer to the overview of design patterns <a href="http://viksrirangam.github.io/blog/design-patterns-overview" title="sofware design patterns using c#" target="_blank">here</a>. The intent of Builder pattern is separating object construction and its represenation. Here builder knows how to build a complex object and we also need a Director class, essentially a helper class which know what to build. Director uses Builder class (one or more builder classes) and helps in building the complex object.</p>

<p>
    <figure>
      <img class="diagram" src="/images/TemplatemethodPattern.png" alt="Template Method Pattern UML Diagram" width="716px" height="185px" />
      <figcaption>Template Method Pattern UML Diagram</figcaption>
    </figure>    
</p>

{% highlight csharp %}

namespace PatternsDemo
{
    public class Portfolio
    {
        List<IAsset> assets = new List<IAsset>();

        int riskAppetiteFactor;

        public int AssessPortfolioRisk()
        {
            return assets.Sum(a => a.AssessRisk(riskAppetiteFactor));
        }
    }

    public absrtact class Asset
    {        
        public abstract int GetRiskScore();

        public int AssessRisk(int personAppetiteFactor)
        {
            return personAppetiteFactor * a.GetRiskScore());
        }
    }

    public class StockAsset : Asset
    {
        public int GetRiskScore()
        {
            return 5;
        }
    }

    public class FixedDepositAsset : Asset
    {
        public int GetRiskScore()
        {
            return 1;
        }
    }
}

{% endhighlight %}