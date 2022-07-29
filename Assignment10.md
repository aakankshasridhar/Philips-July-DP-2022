    using System;
    using System.Collections.Generic;

    public class Image
    {
        public List<Shape> Shapes { get; set; }
        
        public Image()
        {
            Shapes = new List<Shape>();
        }
        
        public void plot(List<ShapePlotter> plotters)
        {
            foreach(Shape shape in shapes)
            {
                foreach(ShapePlotter plotter in plotters)
                {
                    shape.plot(plotter);
                }
            }
        }   
    }

    public abstract class Shape
    {
        public abstract void Plot(ShapePlotter plotter);
    }

    public class Rectangle : Shape
    {
        public string GeHeightAndWidth()
        { 
          
        }
        
        public override void plot(ShapePlotter plotter) 
        {
            plotter.Plot(this);
        }   
    }
    public class Circle : Shape
    {
        public string GetRadius()
        { 
           
        }
        
        public override void plot(ShapePlotter plotter) 
        {
            plotter.Plot(this);
        }   
    }
    
    public class Polygon : Shape
    {
        public string GetSides()
        { 
           
        }
        
        public override void plot(ShapePlotter plotter) 
        {
            plotter.Plot(this);
        }   
    }

    public abstract class ShapePlotter
    {
        public abstract void Plot(Rectangle rectangle);
        public abstract void Plot(Circle circle);
        public abstract void Plot(Polygon polygon);
    }
        

    public class LaserPrinter : ShapePlotter
    {
        public override void Plot(Rectangle rectangle)
        {
            Console.WriteLine("Rectangle using LaserPrinter);
            Console.WriteLine(rectangle.GeHeightAndWidth());
        }
        
        public override void Plot(Circle circle)
        {
            Console.WriteLine("Circle using LaserPrinter);
            Console.WriteLine(circle.GetRadius());
        }
        
        public override void Plot(Polygon polygon)
        {
            Console.WriteLine("Polygon using LaserPrinter);
            Console.WriteLine(polygon.GetSides());
        }
    }

    public class InkJetPrinter : ShapePlotter
    {
        public override void Plot(Rectangle rectangle)
        {
            Console.WriteLine("Rectangle using LaserPrinter);
            Console.WriteLine(rectangle.GeHeightAndWidth());
        }
        
        public override void Plot(Circle circle)
        {
            Console.WriteLine("Circle using LaserPrinter);
            Console.WriteLine(circle.GetRadius());
        }
        
        public override void Plot(Polygon polygon)
        {
            Console.WriteLine("Polygon using LaserPrinter);
            Console.WriteLine(polygon.GetSides());
        }
    }

    public class Program 
    {
        public static void Main() 
        {
            Shape rect = new Rectangle();
            Shape circle = new Circle();
            Shape polygon = new Polygon();
            
            ShapePoltter laserPrinter = new LaserPrinter();
            ShapePoltter inkJetrinter = new InkJetPrinter();
            
            Image image = new Image();
            
            image.Shapes.Add(rect);
            image.Shapes.Add(circle);
            image.Shapes.Add(polygon);
            
            List<ShapePlotter> plotters = new List<ShapePlotter>();
            plotters.Add(laserPrinter);
            plotters.Add(inkJetrinter);
            
            // plotting all shapes
            image.plot(plotters);
        }
    }
