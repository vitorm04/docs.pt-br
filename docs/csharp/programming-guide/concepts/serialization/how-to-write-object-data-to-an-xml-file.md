---
title: Como gravar dados de objeto em um arquivo XML (C#)
ms.date: 07/20/2015
ms.assetid: 7681eb98-703d-4005-a369-26a7bca0f894
ms.openlocfilehash: 475e9398f20a2a4db9fb537d0b8d44f0273e980b
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346445"
---
# <a name="how-to-write-object-data-to-an-xml-file-c"></a><span data-ttu-id="6748b-102">Como gravar dados de objeto em um arquivo XML (C#)</span><span class="sxs-lookup"><span data-stu-id="6748b-102">How to write object data to an XML file (C#)</span></span>
<span data-ttu-id="6748b-103">Este exemplo grava o objeto de uma classe para um arquivo XML usando a classe <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="6748b-103">This example writes the object from a class to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6748b-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6748b-104">Example</span></span>  
  
```csharp  
public class XMLWrite  
{  
  
   static void Main(string[] args)  
    {  
        WriteXML();  
    }  
  
    public class Book  
    {  
        public String title;   
    }  
  
    public static void WriteXML()  
    {  
        Book overview = new Book();  
        overview.title = "Serialization Overview";  
        System.Xml.Serialization.XmlSerializer writer =   
            new System.Xml.Serialization.XmlSerializer(typeof(Book));  
  
        var path = Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments) + "//SerializationOverview.xml";  
        System.IO.FileStream file = System.IO.File.Create(path);  
  
        writer.Serialize(file, overview);  
        file.Close();  
    }  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6748b-105">Compilando o Código</span><span class="sxs-lookup"><span data-stu-id="6748b-105">Compiling the Code</span></span>  
 <span data-ttu-id="6748b-106">A classe precisa ter um construtor público sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="6748b-106">The class being serialized must have a public constructor without parameters.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="6748b-107">Programação Robusta</span><span class="sxs-lookup"><span data-stu-id="6748b-107">Robust Programming</span></span>  
 <span data-ttu-id="6748b-108">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="6748b-108">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="6748b-109">A classe que está sendo serializada não tem um construtor público sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="6748b-109">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
- <span data-ttu-id="6748b-110">O arquivo existe e é somente leitura (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="6748b-110">The file exists and is read-only (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="6748b-111">O caminho é muito longo (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="6748b-111">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="6748b-112">O disco está cheio (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="6748b-112">The disk is full (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="6748b-113">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6748b-113">.NET Framework Security</span></span>  
 <span data-ttu-id="6748b-114">Este exemplo cria um novo arquivo, se o arquivo ainda não existe.</span><span class="sxs-lookup"><span data-stu-id="6748b-114">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="6748b-115">Se um aplicativo precisar criar um arquivo, ele precisará de acesso `Create` para a pasta.</span><span class="sxs-lookup"><span data-stu-id="6748b-115">If an application needs to create a file, that application needs `Create` access for the folder.</span></span> <span data-ttu-id="6748b-116">Se o arquivo já existe, o aplicativo precisa apenas de acesso `Write`, um privilégio menor.</span><span class="sxs-lookup"><span data-stu-id="6748b-116">If the file already exists, the application needs only `Write` access, a lesser privilege.</span></span> <span data-ttu-id="6748b-117">Sempre que possível, é mais seguro criar o arquivo durante a implantação e somente conceder acesso `Read` a um único arquivo, em vez de acesso `Create` a uma pasta.</span><span class="sxs-lookup"><span data-stu-id="6748b-117">Where possible, it is more secure to create the file during deployment, and only grant `Read` access to a single file, rather than `Create` access for a folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6748b-118">Veja também</span><span class="sxs-lookup"><span data-stu-id="6748b-118">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="6748b-119">Como ler dados de objeto de um arquivo XML (C#)</span><span class="sxs-lookup"><span data-stu-id="6748b-119">How to read object data from an XML file (C#)</span></span>](./how-to-read-object-data-from-an-xml-file.md)
- [<span data-ttu-id="6748b-120">Serialização (C#)</span><span class="sxs-lookup"><span data-stu-id="6748b-120">Serialization (C#)</span></span>](./index.md)
