---
title: Objetos de extensão XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: a4ebdbad-087c-4cfe-acc0-17c48142f81a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 25c9c1c81db0bb6775aa9226318d7ec726a93e09
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924932"
---
# <a name="xslt-extension-objects"></a><span data-ttu-id="77cd5-102">Objetos de extensão XSLT</span><span class="sxs-lookup"><span data-stu-id="77cd5-102">XSLT Extension Objects</span></span>
<span data-ttu-id="77cd5-103">Os objetos de extensão são usados para estender a funcionalidade de folhas de estilos.</span><span class="sxs-lookup"><span data-stu-id="77cd5-103">Extension objects are used to extend the functionality of style sheets.</span></span> <span data-ttu-id="77cd5-104">Os objetos de extensão são mantidos pela classe de <xref:System.Xml.Xsl.XsltArgumentList> .</span><span class="sxs-lookup"><span data-stu-id="77cd5-104">Extension objects are maintained by the <xref:System.Xml.Xsl.XsltArgumentList> class.</span></span>  
  
 <span data-ttu-id="77cd5-105">Os seguintes são vantagens de usar um objeto de extensão em vez do script inserido:</span><span class="sxs-lookup"><span data-stu-id="77cd5-105">The following are advantages to using an extension object rather than embedded script:</span></span>  
  
- <span data-ttu-id="77cd5-106">Fornece a melhor encapsulamento e reutilização de classes.</span><span class="sxs-lookup"><span data-stu-id="77cd5-106">Provides better encapsulation and reuse of classes.</span></span>  
  
- <span data-ttu-id="77cd5-107">Permite que as folhas de estilos são menores e mais sustentável.</span><span class="sxs-lookup"><span data-stu-id="77cd5-107">Allows style sheets to be smaller and more maintainable.</span></span>  
  
 <span data-ttu-id="77cd5-108">Os objetos de extensão XSLT são adicionados ao objeto de <xref:System.Xml.Xsl.XsltArgumentList> usando o método <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> .</span><span class="sxs-lookup"><span data-stu-id="77cd5-108">XSLT extension objects are added to the <xref:System.Xml.Xsl.XsltArgumentList> object using the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span> <span data-ttu-id="77cd5-109">Um nome qualificado e URI de namespace são associados com o objeto de extensão no momento.</span><span class="sxs-lookup"><span data-stu-id="77cd5-109">A qualified name and namespace URI are associated with the extension object at that time.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="77cd5-110">O conjunto de permissões FullTrust é necessário chamar o método de <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> .</span><span class="sxs-lookup"><span data-stu-id="77cd5-110">The FullTrust permission set is required to call the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span> <span data-ttu-id="77cd5-111">Para saber mais, confira [Segurança de acesso ao código](../../../../docs/framework/misc/code-access-security.md) e [Conjuntos de permissão nomeada](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="77cd5-111">For more information, see [Code Access Security](../../../../docs/framework/misc/code-access-security.md) and [Named Permission Sets](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100)).</span></span>  
  
 <span data-ttu-id="77cd5-112">Os tipos de dados retornados de objetos de extensão é um dos quatro tipos de dados básicos XPath `number`, `string`, `Boolean`, e `node set`.</span><span class="sxs-lookup"><span data-stu-id="77cd5-112">The data types returned from extension objects are one of the four basic XPath data types of `number`, `string`, `Boolean`, and `node set`.</span></span>  
  
 <span data-ttu-id="77cd5-113">Nenhum método que é definido com a palavra-chave `params` , que permite que um número especificado de parâmetros não é passado, não é suportado atualmente pela classe de <xref:System.Xml.Xsl.XslCompiledTransform> .</span><span class="sxs-lookup"><span data-stu-id="77cd5-113">Any method that is defined with the `params` keyword, which allows an unspecified number of parameters to be passed, is not currently supported by the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="77cd5-114">As folhas de estilos XSLT que utilizam qualquer método definido com a palavra-chave `params` não funcionarão corretamente.</span><span class="sxs-lookup"><span data-stu-id="77cd5-114">XSLT style sheets that utilize any method defined with the `params` keyword will not work correctly.</span></span> <span data-ttu-id="77cd5-115">Para obter detalhes, confira [params](../../../csharp/language-reference/keywords/params.md).</span><span class="sxs-lookup"><span data-stu-id="77cd5-115">For details, see [params](../../../csharp/language-reference/keywords/params.md).</span></span>  
  
### <a name="to-use-an-xslt-extension-object"></a><span data-ttu-id="77cd5-116">Para usar um objeto de extensão XSLT</span><span class="sxs-lookup"><span data-stu-id="77cd5-116">To use an XSLT extension object</span></span>  
  
1. <span data-ttu-id="77cd5-117">Crie um objeto de <xref:System.Xml.Xsl.XsltArgumentList> e adicione o objeto de extensão usando o método <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> .</span><span class="sxs-lookup"><span data-stu-id="77cd5-117">Create an <xref:System.Xml.Xsl.XsltArgumentList> object and add the extension object using <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span>  
  
2. <span data-ttu-id="77cd5-118">Chame o objeto de extensão folha de estilos.</span><span class="sxs-lookup"><span data-stu-id="77cd5-118">Call the extension object from the style sheet.</span></span>  
  
3. <span data-ttu-id="77cd5-119">Passe o objeto de <xref:System.Xml.Xsl.XsltArgumentList> para o método de <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> .</span><span class="sxs-lookup"><span data-stu-id="77cd5-119">Pass the <xref:System.Xml.Xsl.XsltArgumentList> object to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77cd5-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="77cd5-120">See also</span></span>

- [<span data-ttu-id="77cd5-121">Transformações XSLT</span><span class="sxs-lookup"><span data-stu-id="77cd5-121">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)
- [<span data-ttu-id="77cd5-122">Considerações de segurança de XSLT</span><span class="sxs-lookup"><span data-stu-id="77cd5-122">XSLT Security Considerations</span></span>](../../../../docs/standard/data/xml/xslt-security-considerations.md)
