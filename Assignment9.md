![image](https://user-images.githubusercontent.com/53172079/181787423-0e845556-0c97-44be-be9d-f9756e007c2a.png)

    public class Document
    {
        public List<IDocumentPart> DocumentParts { get; set; }

        public void AddDocParts(string header, string footer, string paragraph, string link)
        {
            DocumentParts = new List<IDocumentPart>
            {
                new HeaderPart() {Content = header},
                new FooterPart() {Content = footer},
                new ParagraphPart() {Content = paragraph},
                new LinkPart() {Content = link}
            };
        }

        public void Convert(IDocumentFormat documentFormat)
        {
            foreach (IDocumentPart docPart in DocumentParts)
            {
                docPart.Convert(documentFormat);
            }
        }
    }
    
    public interface IDocumentPart
    {
        string Content { get; set; }
        void Convert(IDocumentFormat format);
    }
    
    public class HeaderPart : IDocumentPart
    {
        public string Content { get; set; }

        public void Convert(IDocumentFormat format)
        {
            format.Convert(this);
        }
    }
    
    public class FooterPart : IDocumentPart
    {
        public string Content { get; set; }

        public void Convert(IDocumentFormat format)
        {
            format.Convert(this);
        }
    }
    
    public class ParagraphPart : IDocumentPart
    {
        public string Content { get; set; }

        public void Convert(IDocumentFormat format)
        {
            format.Convert(this);
        }
    }
    
    public class LinkPart : IDocumentPart
    {
        public string Content { get; set; }

        public void Convert(IDocumentFormat format)
        {
            format.Convert(this);
        }
    }
    
    public interface IDocumentFormat
    {
        void Convert(HeaderPart doc);
        void Convert(FooterPart doc);
        void Convert(ParagraphPart doc);
        void Convert(LinkPart doc);
    }
    
    public class HTMLFormat: IDocumentFormat
    {
        public void Convert(HeaderPart docPart)
        {
        }

        public void Convert(FooterPart docPart)
        {
        }

        public void Convert(ParagraphPart docPart)
        {
        }

        public void Convert(LinkPart docPart)
        {
        }
    }
    
    public class RTFFormat: IDocumentFormat
    {
        public void Convert(HeaderPart docPart)
        {
        }

        public void Convert(FooterPart docPart)
        {
        }

        public void Convert(ParagraphPart docPart)
        {
        }

        public void Convert(LinkPart docPart)
        {
        }
    }
    
    public class PDFFormat: IDocumentFormat
    {
        public void Convert(HeaderPart docPart)
        {
        }

        public void Convert(FooterPart docPart)
        {
        }

        public void Convert(ParagraphPart docPart)
        {
        }

        public void Convert(LinkPart docPart)
        {
        }
    }
    
