---
title: Operador GetXmlNamespace (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.GetXmlNamespace
- GetXmlNamespace
helpviewer_keywords:
- GetXmlNamespace operator [Visual Basic]
- GetXmlNamespace keyword [Visual Basic]
ms.assetid: d0d28cfd-0755-4896-ae0b-4981aa35517c
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 47ba67bc58debf8f144f6468bf510932414c0698
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="getxmlnamespace-operator-visual-basic"></a><span data-ttu-id="a5737-102">Operador GetXmlNamespace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a5737-102">GetXmlNamespace Operator (Visual Basic)</span></span>
<span data-ttu-id="a5737-103">Obtém o <xref:System.Xml.Linq.XNamespace> objeto correspondente para o prefixo de namespace XML especificado.</span><span class="sxs-lookup"><span data-stu-id="a5737-103">Gets the <xref:System.Xml.Linq.XNamespace> object that corresponds to the specified XML namespace prefix.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5737-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a5737-104">Syntax</span></span>  
  
```  
GetXmlNamespace(xmlNamespacePrefix)  
```  
  
## <a name="parts"></a><span data-ttu-id="a5737-105">Partes</span><span class="sxs-lookup"><span data-stu-id="a5737-105">Parts</span></span>  
 `xmlNamespacePrefix`  
 <span data-ttu-id="a5737-106">Opcional.</span><span class="sxs-lookup"><span data-stu-id="a5737-106">Optional.</span></span> <span data-ttu-id="a5737-107">A cadeia de caracteres que identifica o prefixo de namespace XML.</span><span class="sxs-lookup"><span data-stu-id="a5737-107">The string that identifies the XML namespace prefix.</span></span> <span data-ttu-id="a5737-108">Se fornecido, essa cadeia de caracteres deve ser um identificador XML válido.</span><span class="sxs-lookup"><span data-stu-id="a5737-108">If supplied, this string must be a valid XML identifier.</span></span> <span data-ttu-id="a5737-109">Para obter mais informações, consulte [nomes de declarado elementos e atributos XML](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="a5737-109">For more information, see [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span> <span data-ttu-id="a5737-110">Se nenhum prefixo for especificado, o namespace padrão será retornado.</span><span class="sxs-lookup"><span data-stu-id="a5737-110">If no prefix is specified, the default namespace is returned.</span></span> <span data-ttu-id="a5737-111">Se nenhum namespace padrão for especificado, o namespace vazio será retornado.</span><span class="sxs-lookup"><span data-stu-id="a5737-111">If no default namespace is specified, the empty namespace is returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a5737-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="a5737-112">Return Value</span></span>  
 <span data-ttu-id="a5737-113">O <xref:System.Xml.Linq.XNamespace> objeto que corresponde ao prefixo de namespace XML.</span><span class="sxs-lookup"><span data-stu-id="a5737-113">The <xref:System.Xml.Linq.XNamespace> object that corresponds to the XML namespace prefix.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a5737-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="a5737-114">Remarks</span></span>  
 <span data-ttu-id="a5737-115">O `GetXmlNamespace` operador obtém o <xref:System.Xml.Linq.XNamespace> objeto que corresponde ao prefixo de namespace XML `xmlNamespacePrefix`.</span><span class="sxs-lookup"><span data-stu-id="a5737-115">The `GetXmlNamespace` operator gets the <xref:System.Xml.Linq.XNamespace> object that corresponds to the XML namespace prefix `xmlNamespacePrefix`.</span></span>  
  
 <span data-ttu-id="a5737-116">Você pode usar prefixos de namespace XML diretamente em literais XML e propriedades de eixo XML.</span><span class="sxs-lookup"><span data-stu-id="a5737-116">You can use XML namespace prefixes directly in XML literals and XML axis properties.</span></span> <span data-ttu-id="a5737-117">No entanto, você deve usar o `GetXmlNamespace` para converter um prefixo de namespace para um <xref:System.Xml.Linq.XNamespace> objeto antes de você pode usá-lo em seu código.</span><span class="sxs-lookup"><span data-stu-id="a5737-117">However, you must use the `GetXmlNamespace` operator to convert a namespace prefix to an <xref:System.Xml.Linq.XNamespace> object before you can use it in your code.</span></span> <span data-ttu-id="a5737-118">Você pode acrescentar um nome de elemento não qualificado para um <xref:System.Xml.Linq.XNamespace> objeto para obter um totalmente qualificado <xref:System.Xml.Linq.XName> do objeto, que muitos [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] métodos requerem.</span><span class="sxs-lookup"><span data-stu-id="a5737-118">You can append an unqualified element name to an <xref:System.Xml.Linq.XNamespace> object to get a fully qualified <xref:System.Xml.Linq.XName> object, which many [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] methods require.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5737-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a5737-119">Example</span></span>  
 <span data-ttu-id="a5737-120">O exemplo a seguir importa `ns` como um prefixo de namespace XML.</span><span class="sxs-lookup"><span data-stu-id="a5737-120">The following example imports `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="a5737-121">Ele usa o prefixo de namespace para criar um literal XML e acessar o primeiro nó filho que tem o nome qualificado `ns:phone`.</span><span class="sxs-lookup"><span data-stu-id="a5737-121">It then uses the prefix of the namespace to create an XML literal and access the first child node that has the qualified name `ns:phone`.</span></span> <span data-ttu-id="a5737-122">Em seguida, passar esse nó filho para o `ShowName` sub-rotina, que constrói um nome qualificado usando o `GetXmlNamespace` operador.</span><span class="sxs-lookup"><span data-stu-id="a5737-122">It then passes that child node to the `ShowName` subroutine, which constructs a qualified name by using the `GetXmlNamespace` operator.</span></span> <span data-ttu-id="a5737-123">O `ShowName` sub-rotina, em seguida, passa o nome qualificado para o <xref:System.Xml.Linq.XNode.Ancestors%2A> método para obter o pai `ns:contact` nó.</span><span class="sxs-lookup"><span data-stu-id="a5737-123">The `ShowName` subroutine then passes the qualified name to the <xref:System.Xml.Linq.XNode.Ancestors%2A> method to get the parent `ns:contact` node.</span></span>  
  
 [!code-vb[VbXMLSamples#38](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/getxmlnamespace-operator_1.vb)]  
  
 <span data-ttu-id="a5737-124">Quando você chama `TestGetXmlNamespace.RunSample()`, ele exibe uma caixa de mensagem que contém o seguinte texto:</span><span class="sxs-lookup"><span data-stu-id="a5737-124">When you call `TestGetXmlNamespace.RunSample()`, it displays a message box that contains the following text:</span></span>  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="a5737-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a5737-125">See Also</span></span>  
 [<span data-ttu-id="a5737-126">Instrução Imports (Namespace de XML)</span><span class="sxs-lookup"><span data-stu-id="a5737-126">Imports Statement (XML Namespace)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)  
 [<span data-ttu-id="a5737-127">Acessando XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a5737-127">Accessing XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
