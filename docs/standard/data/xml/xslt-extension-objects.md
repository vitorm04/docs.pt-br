---
title: Objetos de extensão XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: a4ebdbad-087c-4cfe-acc0-17c48142f81a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 69fcd4bd8426bb349c090fc52f7a1f1a262378ea
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33570478"
---
# <a name="xslt-extension-objects"></a><span data-ttu-id="a2ad8-102">Objetos de extensão XSLT</span><span class="sxs-lookup"><span data-stu-id="a2ad8-102">XSLT Extension Objects</span></span>
<span data-ttu-id="a2ad8-103">Os objetos de extensão são usados para estender a funcionalidade de folhas de estilos.</span><span class="sxs-lookup"><span data-stu-id="a2ad8-103">Extension objects are used to extend the functionality of style sheets.</span></span> <span data-ttu-id="a2ad8-104">Os objetos de extensão são mantidos pela classe de <xref:System.Xml.Xsl.XsltArgumentList> .</span><span class="sxs-lookup"><span data-stu-id="a2ad8-104">Extension objects are maintained by the <xref:System.Xml.Xsl.XsltArgumentList> class.</span></span>  
  
 <span data-ttu-id="a2ad8-105">Os seguintes são vantagens de usar um objeto de extensão em vez do script inserido:</span><span class="sxs-lookup"><span data-stu-id="a2ad8-105">The following are advantages to using an extension object rather than embedded script:</span></span>  
  
-   <span data-ttu-id="a2ad8-106">Fornece a melhor encapsulamento e reutilização de classes.</span><span class="sxs-lookup"><span data-stu-id="a2ad8-106">Provides better encapsulation and reuse of classes.</span></span>  
  
-   <span data-ttu-id="a2ad8-107">Permite que as folhas de estilos são menores e mais sustentável.</span><span class="sxs-lookup"><span data-stu-id="a2ad8-107">Allows style sheets to be smaller and more maintainable.</span></span>  
  
 <span data-ttu-id="a2ad8-108">Os objetos de extensão XSLT são adicionados ao objeto de <xref:System.Xml.Xsl.XsltArgumentList> usando o método <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> .</span><span class="sxs-lookup"><span data-stu-id="a2ad8-108">XSLT extension objects are added to the <xref:System.Xml.Xsl.XsltArgumentList> object using the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span> <span data-ttu-id="a2ad8-109">Um nome qualificado e URI de namespace são associados com o objeto de extensão no momento.</span><span class="sxs-lookup"><span data-stu-id="a2ad8-109">A qualified name and namespace URI are associated with the extension object at that time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a2ad8-110">O conjunto de permissões FullTrust é necessário chamar o método de <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> .</span><span class="sxs-lookup"><span data-stu-id="a2ad8-110">The FullTrust permission set is required to call the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span> <span data-ttu-id="a2ad8-111">Para saber mais, confira [Segurança de acesso ao código](http://msdn.microsoft.com/library/23a20143-241d-4fe5-9d9f-3933fd594c03) e [NIB: conjuntos de permissão nomeada](https://msdn.microsoft.com/library/08250d67-c99d-4ab0-8d2b-b0e12019f6e3).</span><span class="sxs-lookup"><span data-stu-id="a2ad8-111">For more information, see [Code Access Security](http://msdn.microsoft.com/library/23a20143-241d-4fe5-9d9f-3933fd594c03) and [NIB: Named Permission Sets](https://msdn.microsoft.com/library/08250d67-c99d-4ab0-8d2b-b0e12019f6e3).</span></span>  
  
 <span data-ttu-id="a2ad8-112">Os tipos de dados retornados de objetos de extensão é um dos quatro tipos de dados básicos XPath `number`, `string`, `Boolean`, e `node set`.</span><span class="sxs-lookup"><span data-stu-id="a2ad8-112">The data types returned from extension objects are one of the four basic XPath data types of `number`, `string`, `Boolean`, and `node set`.</span></span>  
  
 <span data-ttu-id="a2ad8-113">Nenhum método que é definido com a palavra-chave `params` , que permite que um número especificado de parâmetros não é passado, não é suportado atualmente pela classe de <xref:System.Xml.Xsl.XslCompiledTransform> .</span><span class="sxs-lookup"><span data-stu-id="a2ad8-113">Any method that is defined with the `params` keyword, which allows an unspecified number of parameters to be passed, is not currently supported by the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="a2ad8-114">As folhas de estilos XSLT que utilizam qualquer método definido com a palavra-chave `params` não funcionarão corretamente.</span><span class="sxs-lookup"><span data-stu-id="a2ad8-114">XSLT style sheets that utilize any method defined with the `params` keyword will not work correctly.</span></span> <span data-ttu-id="a2ad8-115">Para obter detalhes, confira [params](~/docs/csharp/language-reference/keywords/params.md).</span><span class="sxs-lookup"><span data-stu-id="a2ad8-115">For details, see [params](~/docs/csharp/language-reference/keywords/params.md).</span></span>  
  
### <a name="to-use-an-xslt-extension-object"></a><span data-ttu-id="a2ad8-116">Para usar um objeto de extensão XSLT</span><span class="sxs-lookup"><span data-stu-id="a2ad8-116">To use an XSLT extension object</span></span>  
  
1.  <span data-ttu-id="a2ad8-117">Crie um objeto de <xref:System.Xml.Xsl.XsltArgumentList> e adicione o objeto de extensão usando o método <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> .</span><span class="sxs-lookup"><span data-stu-id="a2ad8-117">Create an <xref:System.Xml.Xsl.XsltArgumentList> object and add the extension object using <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span>  
  
2.  <span data-ttu-id="a2ad8-118">Chame o objeto de extensão folha de estilos.</span><span class="sxs-lookup"><span data-stu-id="a2ad8-118">Call the extension object from the style sheet.</span></span>  
  
3.  <span data-ttu-id="a2ad8-119">Passe o objeto de <xref:System.Xml.Xsl.XsltArgumentList> para o método de <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> .</span><span class="sxs-lookup"><span data-stu-id="a2ad8-119">Pass the <xref:System.Xml.Xsl.XsltArgumentList> object to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2ad8-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a2ad8-120">See Also</span></span>  
 [<span data-ttu-id="a2ad8-121">Transformações XSLT</span><span class="sxs-lookup"><span data-stu-id="a2ad8-121">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)  
 [<span data-ttu-id="a2ad8-122">Considerações de segurança de XSLT</span><span class="sxs-lookup"><span data-stu-id="a2ad8-122">XSLT Security Considerations</span></span>](../../../../docs/standard/data/xml/xslt-security-considerations.md)
