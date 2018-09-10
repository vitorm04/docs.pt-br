---
title: Como executar uma transformação XSLT usando um assembly
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 76ee440b-d134-4f8f-8262-b917ad6dcbf6
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ef0d47ae18b8bdd3f1d49a20937b65e9872ab551
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/09/2018
ms.locfileid: "44201745"
---
# <a name="how-to-perform-an-xslt-transformation-by-using-an-assembly"></a><span data-ttu-id="b088a-102">Como executar uma transformação XSLT usando um assembly</span><span class="sxs-lookup"><span data-stu-id="b088a-102">How to: Perform an XSLT Transformation by Using an Assembly</span></span>
<span data-ttu-id="b088a-103">O compilador XSLT (xsltc.exe) compila folhas de estilos XSLT e gera um assembly.</span><span class="sxs-lookup"><span data-stu-id="b088a-103">The XSLT compiler (xsltc.exe) compiles XSLT style sheets and generates an assembly.</span></span> <span data-ttu-id="b088a-104">O assembly pode ser passado diretamente no método <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b088a-104">The assembly can be passed directly into the <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> method.</span></span>  
  
### <a name="to-copy-the-xml-and-xslt-files-to-your-local-computer"></a><span data-ttu-id="b088a-105">Para copiar os arquivos XML e XSLT para seu computador local</span><span class="sxs-lookup"><span data-stu-id="b088a-105">To copy the XML and XSLT files to your local computer</span></span>  
  
-   <span data-ttu-id="b088a-106">Copie o arquivo XSLT para seu computador local e nomeie-o Transform.xsl.</span><span class="sxs-lookup"><span data-stu-id="b088a-106">Copy the XSLT file to your local computer and name it Transform.xsl.</span></span>  
  
    ```xml  
    <xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
      xmlns:msxsl="urn:schemas-microsoft-com:xslt"  
      xmlns:user="urn:my-scripts">  
      <msxsl:script language="C#" implements-prefix="user">  
        <![CDATA[  
      public string discount(string price){  
        char[] trimChars = { '$' };  
        //trim leading $, convert price to type double  
        double discount_value = Convert.ToDouble(price.TrimStart(trimChars));  
        //apply 10% discount and round appropriately  
        discount_value = .9*discount_value;  
        //convert value to decimal and format as currency  
        string discount_price = discount_value.ToString("C");  
        return discount_price;  
      }  
      ]]>  
      </msxsl:script>  
      <xsl:template match="catalog">  
        <html>  
          <head></head>  
          <body>  
            <table border="1">  
              <tr>  
                <th align="left">Title</th>  
                <th align="left">Author</th>  
                <th align="left">Genre</th>  
                <th align="left">Publish Date</th>  
                <th align="left">Price</th>  
              </tr>  
              <xsl:for-each select="book">  
                <tr>  
                  <td>  
                    <xsl:value-of select="title"/>  
                  </td>  
                  <td>  
                    <xsl:value-of select="author"/>  
                  </td>  
                  <td>  
                    <xsl:value-of select="genre"/>  
                  </td>  
                  <td>  
                    <xsl:value-of select="publish_date"/>  
                  </td>  
                  <xsl:choose>  
                    <xsl:when test="genre = 'Fantasy'">  
                      <td>  
                        <xsl:value-of select="user:discount(price)"/>  
                      </td>  
                    </xsl:when>  
                    <xsl:otherwise>  
                      <td>  
                        <xsl:value-of select="price"/>  
                      </td>  
                    </xsl:otherwise>  
                  </xsl:choose>  
                </tr>  
              </xsl:for-each>  
            </table>  
          </body>  
        </html>  
      </xsl:template>  
    </xsl:stylesheet>  
    ```  
  
-   <span data-ttu-id="b088a-107">Copie o arquivo XML para seu computador local e nomeie-o `books.xml`.</span><span class="sxs-lookup"><span data-stu-id="b088a-107">Copy the XML file to your local computer and name it `books.xml`.</span></span>  
  
    ```xml  
    <?xml version="1.0"?>  
    <catalog>  
       <book id="bk101">  
          <author>Gambardella, Matthew</author>  
          <title>XML Developer's Guide</title>  
          <genre>Computer</genre>  
          <price>$44.95</price>  
          <publish_date>2000-10-01</publish_date>  
       </book>  
       <book id="bk102">  
          <author>Ralls, Kim</author>  
          <title>Midnight Rain</title>  
          <genre>Fantasy</genre>  
          <price>$5.95</price>  
          <publish_date>2000-12-16</publish_date>  
       </book>  
       <book id="bk103">  
          <author>Corets, Eva</author>  
          <title>Maeve Ascendant</title>  
          <genre>Fantasy</genre>  
          <price>$5.95</price>  
          <publish_date>2000-11-17</publish_date>  
       </book>  
       <book id="bk106">  
          <author>Randall, Cynthia</author>  
          <title>Lover Birds</title>  
          <genre>Romance</genre>  
          <price>$4.95</price>  
          <publish_date>2000-09-02</publish_date>  
       </book>  
       <book id="bk107">  
          <author>Thurman, Paula</author>  
          <title>Splish Splash</title>  
          <genre>Romance</genre>  
          <price>$4.95</price>  
          <publish_date>2000-11-02</publish_date>  
       </book>  
    </catalog>  
    ```  
  
### <a name="to-compile-the-style-sheet-with-the-script-enabled"></a><span data-ttu-id="b088a-108">Para compilar a folha de estilos com o script habilitado.</span><span class="sxs-lookup"><span data-stu-id="b088a-108">To compile the style sheet with the script enabled.</span></span>  
  
1.  <span data-ttu-id="b088a-109">A execução do comando a seguir a partir da linha de comando cria dois assemblies nomeados `Transform.dll` e `Transform_Script1.dll` (Esse é o comportamento padrão.</span><span class="sxs-lookup"><span data-stu-id="b088a-109">Executing the following command from the command line creates two assemblies named `Transform.dll` and `Transform_Script1.dll` (This is the default behavior.</span></span> <span data-ttu-id="b088a-110">A menos que de outra forma especificado, o nome da classe e do assembly usa como padrão o nome da folha de estilos principal):</span><span class="sxs-lookup"><span data-stu-id="b088a-110">Unless otherwise specified, the name of the class and the assembly defaults to the name of the main style sheet):</span></span>  
  
    ```  
    xsltc /settings:script+ Transform.xsl  
    ```  
  
 <span data-ttu-id="b088a-111">O comando a seguir define explicitamente o nome da classe como Transform:</span><span class="sxs-lookup"><span data-stu-id="b088a-111">The following command explicitly sets the class name to Transform:</span></span>  
  
```  
xsltc /settings:script+ /class:Transform Transform.xsl  
```  
  
### <a name="to-include-the-compiled-assembly-as-a-reference-when-you-compile-your-code"></a><span data-ttu-id="b088a-112">Para incluir o assembly compilado como uma referência ao compilar o código.</span><span class="sxs-lookup"><span data-stu-id="b088a-112">To include the compiled assembly as a reference when you compile your code.</span></span>  
  
1.  <span data-ttu-id="b088a-113">Você pode incluir um assembly no Visual Studio adicionando uma referência do Gerenciador de Soluções ou da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="b088a-113">You can include an assembly in Visual Studio by adding a reference in the Solution Explorer, or from the command line.</span></span>  
  
2.  <span data-ttu-id="b088a-114">Para a linha de comando com C#, use o seguinte:</span><span class="sxs-lookup"><span data-stu-id="b088a-114">For the command line with C#, use the following:</span></span>  
  
    ```  
    csc myCode.cs /r:system.dll;system.xml.dll;Transform.dll  
    ```  
  
3.  <span data-ttu-id="b088a-115">Para a linha de comando com Visual Basic, use o seguinte:</span><span class="sxs-lookup"><span data-stu-id="b088a-115">For the command line with Visual Basic, use the following</span></span>  
  
    ```  
    vbc myCode.vb /r:system.dll;system.xml.dll;Transform.dll  
    ```  
  
### <a name="to-use-the-compiled-assembly-in-your-code"></a><span data-ttu-id="b088a-116">Para usar o assembly compilado em seu código.</span><span class="sxs-lookup"><span data-stu-id="b088a-116">To use the compiled assembly in your code.</span></span>  
  
1.  <span data-ttu-id="b088a-117">O exemplo a seguir mostra como executar a transformação XSLT usando a folha de estilos compilada.</span><span class="sxs-lookup"><span data-stu-id="b088a-117">The following example shows how to execute the XSLT transformation by using the compiled style sheet.</span></span>  
  
 [!code-csharp[XslTransform_XSLTC#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XslTransform_XSLTC/CS/XslTransform_XSLTC.cs#1)]
 [!code-vb[XslTransform_XSLTC#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslTransform_XSLTC/VB/XslTransform_XSLTC.vb#1)]  
  
 <span data-ttu-id="b088a-118">Para vincular ao assembly compilado dinamicamente, substitua</span><span class="sxs-lookup"><span data-stu-id="b088a-118">To dynamically link to the compiled assembly, replace</span></span>  
  
```  
xslt.Load(typeof(Transform))  
```  
  
 <span data-ttu-id="b088a-119">with</span><span class="sxs-lookup"><span data-stu-id="b088a-119">with</span></span>  
  
```  
xslt.Load(System.Reflection.Assembly.Load("Transform").GetType("Transform"))  
```  
  
 <span data-ttu-id="b088a-120">no exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="b088a-120">in the example above.</span></span> <span data-ttu-id="b088a-121">Para obter mais informações sobre o método Assembly.Load, consulte <xref:System.Reflection.Assembly.Load%2A></span><span class="sxs-lookup"><span data-stu-id="b088a-121">For more information on the Assembly.Load method, see <xref:System.Reflection.Assembly.Load%2A></span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b088a-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b088a-122">See also</span></span>

- <xref:System.Xml.Xsl.XslCompiledTransform>  
- [<span data-ttu-id="b088a-123">Compilador de XSLT (xsltc.exe)</span><span class="sxs-lookup"><span data-stu-id="b088a-123">XSLT Compiler (xsltc.exe)</span></span>](../../../../docs/standard/data/xml/xslt-compiler-xsltc-exe.md)  
- [<span data-ttu-id="b088a-124">Transformações XSLT</span><span class="sxs-lookup"><span data-stu-id="b088a-124">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)  
- [<span data-ttu-id="b088a-125">Build pela linha de comando com csc.exe</span><span class="sxs-lookup"><span data-stu-id="b088a-125">Command-line Building With csc.exe</span></span>](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)
