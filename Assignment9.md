![image](https://user-images.githubusercontent.com/53172079/181473764-8096c210-6af2-49af-b0af-798146d69810.png)

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
            format.ConvertHeader(this);
        }
    }
    
    public class FooterPart : IDocumentPart
    {
        public string Content { get; set; }

        public void Convert(IDocumentFormat format)
        {
            format.ConvertFooter(this);
        }
    }
    
    public class ParagraphPart : IDocumentPart
    {
        public string Content { get; set; }

        public void Convert(IDocumentFormat format)
        {
            format.ConvertParagraph(this);
        }
    }
    
    public class LinkPart : IDocumentPart
    {
        public string Content { get; set; }

        public void Convert(IDocumentFormat format)
        {
            format.ConvertLink(this);
        }
    }
    
    public interface IDocumentFormat
    {
        void ConvertHeader(IDocumentPart doc);
        void ConvertFooter(IDocumentPart doc);
        void ConvertParagraph(IDocumentPart doc);
        void ConvertLink(IDocumentPart doc);
    }
    
    public class HTMLFormat: IDocumentFormat
    {
        public void ConvertHeader(IDocumentPart docPart)
        {
        }

        public void ConvertFooter(IDocumentPart docPart)
        {
        }

        public void ConvertParagraph(IDocumentPart docPart)
        {
        }

        public void ConvertLink(IDocumentPart docPart)
        {
        }
    }
    
    public class RTFFormat: IDocumentFormat
    {
        public void ConvertHeader(IDocumentPart docPart)
        {
        }

        public void ConvertFooter(IDocumentPart docPart)
        {
        }

        public void ConvertParagraph(IDocumentPart docPart)
        {
        }

        public void ConvertLink(IDocumentPart docPart)
        {
        }
    }
    
    public class PDFFormat: IDocumentFormat
    {
        public void ConvertHeader(IDocumentPart docPart)
        {
        }

        public void ConvertFooter(IDocumentPart docPart)
        {
        }

        public void ConvertParagraph(IDocumentPart docPart)
        {
        }

        public void ConvertLink(IDocumentPart docPart)
        {
        }
    }
    
