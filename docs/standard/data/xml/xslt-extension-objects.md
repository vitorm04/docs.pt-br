---
title: Objetos de extensão XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: a4ebdbad-087c-4cfe-acc0-17c48142f81a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ab96d5bdefee0cd85d98174f8f7410e940cb12b4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54498366"
---
# <a name="xslt-extension-objects"></a><span data-ttu-id="cba6f-102">Objetos de extensão XSLT</span><span class="sxs-lookup"><span data-stu-id="cba6f-102">XSLT Extension Objects</span></span>
<span data-ttu-id="cba6f-103">Os objetos de extensão são usados para estender a funcionalidade de folhas de estilos.</span><span class="sxs-lookup"><span data-stu-id="cba6f-103">Extension objects are used to extend the functionality of style sheets.</span></span> <span data-ttu-id="cba6f-104">Os objetos de extensão são mantidos pela classe de <xref:System.Xml.Xsl.XsltArgumentList> .</span><span class="sxs-lookup"><span data-stu-id="cba6f-104">Extension objects are maintained by the <xref:System.Xml.Xsl.XsltArgumentList> class.</span></span>  
  
 <span data-ttu-id="cba6f-105">Os seguintes são vantagens de usar um objeto de extensão em vez do script inserido:</span><span class="sxs-lookup"><span data-stu-id="cba6f-105">The following are advantages to using an extension object rather than embedded script:</span></span>  
  
-   <span data-ttu-id="cba6f-106">Fornece a melhor encapsulamento e reutilização de classes.</span><span class="sxs-lookup"><span data-stu-id="cba6f-106">Provides better encapsulation and reuse of classes.</span></span>  
  
-   <span data-ttu-id="cba6f-107">Permite que as folhas de estilos são menores e mais sustentável.</span><span class="sxs-lookup"><span data-stu-id="cba6f-107">Allows style sheets to be smaller and more maintainable.</span></span>  
  
 <span data-ttu-id="cba6f-108">Os objetos de extensão XSLT são adicionados ao objeto de <xref:System.Xml.Xsl.XsltArgumentList> usando o método <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> .</span><span class="sxs-lookup"><span data-stu-id="cba6f-108">XSLT extension objects are added to the <xref:System.Xml.Xsl.XsltArgumentList> object using the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span> <span data-ttu-id="cba6f-109">Um nome qualificado e URI de namespace são associados com o objeto de extensão no momento.</span><span class="sxs-lookup"><span data-stu-id="cba6f-109">A qualified name and namespace URI are associated with the extension object at that time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cba6f-110">O conjunto de permissões FullTrust é necessário chamar o método de <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> .</span><span class="sxs-lookup"><span data-stu-id="cba6f-110">The FullTrust permission set is required to call the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span> <span data-ttu-id="cba6f-111">Para obter mais informações, confira [Segurança de acesso do código](../../../../docs/framework/misc/code-access-security.md) e [NIB: conjuntos de permissões nomeadas](https://msdn.microsoft.com/library/08250d67-c99d-4ab0-8d2b-b0e12019f6e3).</span><span class="sxs-lookup"><span data-stu-id="cba6f-111">For more information, see [Code Access Security](../../../../docs/framework/misc/code-access-security.md) and [NIB: Named Permission Sets](https://msdn.microsoft.com/library/08250d67-c99d-4ab0-8d2b-b0e12019f6e3).</span></span>  
  
 <span data-ttu-id="cba6f-112">Os tipos de dados retornados de objetos de extensão é um dos quatro tipos de dados básicos XPath `number`, `string`, `Boolean`, e `node set`.</span><span class="sxs-lookup"><span data-stu-id="cba6f-112">The data types returned from extension objects are one of the four basic XPath data types of `number`, `string`, `Boolean`, and `node set`.</span></span>  
  
 <span data-ttu-id="cba6f-113">Nenhum método que é definido com a palavra-chave `params` , que permite que um número especificado de parâmetros não é passado, não é suportado atualmente pela classe de <xref:System.Xml.Xsl.XslCompiledTransform> .</span><span class="sxs-lookup"><span data-stu-id="cba6f-113">Any method that is defined with the `params` keyword, which allows an unspecified number of parameters to be passed, is not currently supported by the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="cba6f-114">As folhas de estilos XSLT que utilizam qualquer método definido com a palavra-chave `params` não funcionarão corretamente.</span><span class="sxs-lookup"><span data-stu-id="cba6f-114">XSLT style sheets that utilize any method defined with the `params` keyword will not work correctly.</span></span> <span data-ttu-id="cba6f-115">Para obter detalhes, confira [params](~/docs/csharp/language-reference/keywords/params.md).</span><span class="sxs-lookup"><span data-stu-id="cba6f-115">For details, see [params](~/docs/csharp/language-reference/keywords/params.md).</span></span>  
  
### <a name="to-use-an-xslt-extension-object"></a><span data-ttu-id="cba6f-116">Para usar um objeto de extensão XSLT</span><span class="sxs-lookup"><span data-stu-id="cba6f-116">To use an XSLT extension object</span></span>  
  
1.  <span data-ttu-id="cba6f-117">Crie um objeto de <xref:System.Xml.Xsl.XsltArgumentList> e adicione o objeto de extensão usando o método <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> .</span><span class="sxs-lookup"><span data-stu-id="cba6f-117">Create an <xref:System.Xml.Xsl.XsltArgumentList> object and add the extension object using <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span>  
  
2.  <span data-ttu-id="cba6f-118">Chame o objeto de extensão folha de estilos.</span><span class="sxs-lookup"><span data-stu-id="cba6f-118">Call the extension object from the style sheet.</span></span>  
  
3.  <span data-ttu-id="cba6f-119">Passe o objeto de <xref:System.Xml.Xsl.XsltArgumentList> para o método de <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> .</span><span class="sxs-lookup"><span data-stu-id="cba6f-119">Pass the <xref:System.Xml.Xsl.XsltArgumentList> object to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cba6f-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cba6f-120">See also</span></span>

- [<span data-ttu-id="cba6f-121">Transformações XSLT</span><span class="sxs-lookup"><span data-stu-id="cba6f-121">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)
- [<span data-ttu-id="cba6f-122">Considerações de segurança de XSLT</span><span class="sxs-lookup"><span data-stu-id="cba6f-122">XSLT Security Considerations</span></span>](../../../../docs/standard/data/xml/xslt-security-considerations.md)
