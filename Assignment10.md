Image Plotting Problem

<img width="400" alt="image" src="https://user-images.githubusercontent.com/53172079/181820734-952646a4-83b2-4f06-adc6-e9b2658978be.png">
    
    using System;
    using System.Collections.Generic;

    public class Program 
    {
        public static void Main() 
        {
            Shape rectangle = new Rectangle();
            Shape circle = new Circle();
            Shape polygon = new Polygon();
            
            ShapePrinter laserPrinter = new LaserPrinter();
            ShapePrinter inkJetrinter = new InkJetPrinter();
            
            Image image = new Image();
            
            image.Shapes.Add(rectangle);
            image.Shapes.Add(circle);
            image.Shapes.Add(polygon);
            
            List<ShapePrinter> printes = new List<ShapePrinter>();
            plotters.Add(laserPrinter);
            plotters.Add(inkJetrinter);
            
            image.plot(printes);
        }
    }

    public class Image
    {
        public List<Shape> Shapes { get; set; }
        
        public Image()
        {
            Shapes = new List<Shape>();
        }
        
        public void Plot(List<ShapePrinter> printers)
        {
            foreach(Shape shape in shapes)
            {
                foreach(ShapePrinter printer in printers)
                {
                    shape.plot(printer);
                }
            }
        }   
    }

    public abstract class Shape
    {
        public abstract void Plot(ShapePrinter printer);
    }

    public class Rectangle : Shape
    {
        public string GeHeightAndWidth()
        { 
            return "R.H.W";
        }
        
        public override void Plot(ShapePrinter printer) 
        {
            printer.Plot(this);
        }   
    }
    
    public class Circle : Shape
    {
        public string GetRadius()
        { 
            return "C.R";   
        }
        
        public override void Plot(ShapePrinter printer) 
        {
            printer.Plot(this);
        }   
    }
    
    public class Polygon : Shape
    {
        public string GetSides()
        { 
            return "P.S";
        }
        
        public override void Plot(ShapePrinter printer) 
        {
            printer.Plot(this);
        }   
    }

    public abstract class ShapePrinter
    {
        public abstract void Plot(Rectangle rectangle);
        public abstract void Plot(Circle circle);
        public abstract void Plot(Polygon polygon);
    }
        

    public class LaserPrinter : ShapePrinter
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

    public class InkJetPrinter : ShapePrinter
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
    
Double Dispatch Problem

using System;

public class A
{
    public virtual void M(IVisitor visitor)
    {
        visitor.Visit(this);
        Console.WriteLine("A.M");
    }
}

public class B : A
{
    public override void M(IVisitor visitor)
    {
        visitor.Visit(this);
        Console.WriteLine("B.M");
    }
}

public interface IVisitor
{
    void Visit(B item);
    void Visit(A item);
}

public sealed class Visitor : IVisitor
{
    public void Visit(A item)
    {
        Console.WriteLine("C.A.N");
    }

    public void Visit(B item)
    {
        Console.WriteLine("C.B.N");
    }
}

public class Program
{
    public static void Main()
    {
        var visitor = new Visitor();
        A obj=new B();
        obj.M(visitor);
    }
}
