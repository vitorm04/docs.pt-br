---
title: Operador GetXmlNamespace (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.GetXmlNamespace
- GetXmlNamespace
dev_langs:
- VB
helpviewer_keywords:
- GetXmlNamespace operator
- GetXmlNamespace keyword
ms.assetid: d0d28cfd-0755-4896-ae0b-4981aa35517c
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: d6f977ab8c0b7dfb2dee936436ef4ec8530ba8f6
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="getxmlnamespace-operator-visual-basic"></a><span data-ttu-id="25434-102">Operador GetXmlNamespace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="25434-102">GetXmlNamespace Operator (Visual Basic)</span></span>
<span data-ttu-id="25434-103">Obtém o <xref:System.Xml.Linq.XNamespace>objeto que corresponde ao prefixo do namespace XML especificado.</xref:System.Xml.Linq.XNamespace></span><span class="sxs-lookup"><span data-stu-id="25434-103">Gets the <xref:System.Xml.Linq.XNamespace> object that corresponds to the specified XML namespace prefix.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25434-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="25434-104">Syntax</span></span>  
  
```  
GetXmlNamespace(xmlNamespacePrefix)  
```  
  
## <a name="parts"></a><span data-ttu-id="25434-105">Partes</span><span class="sxs-lookup"><span data-stu-id="25434-105">Parts</span></span>  
 `xmlNamespacePrefix`  
 <span data-ttu-id="25434-106">Opcional.</span><span class="sxs-lookup"><span data-stu-id="25434-106">Optional.</span></span> <span data-ttu-id="25434-107">A cadeia de caracteres que identifica o prefixo de namespace XML.</span><span class="sxs-lookup"><span data-stu-id="25434-107">The string that identifies the XML namespace prefix.</span></span> <span data-ttu-id="25434-108">Se for fornecido, essa cadeia de caracteres deve ser um identificador XML válido.</span><span class="sxs-lookup"><span data-stu-id="25434-108">If supplied, this string must be a valid XML identifier.</span></span> <span data-ttu-id="25434-109">Para obter mais informações, consulte [nomes de declarado elementos e atributos XML](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="25434-109">For more information, see [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span> <span data-ttu-id="25434-110">Se nenhum prefixo for especificado, o namespace padrão é retornado.</span><span class="sxs-lookup"><span data-stu-id="25434-110">If no prefix is specified, the default namespace is returned.</span></span> <span data-ttu-id="25434-111">Se nenhum namespace padrão é especificado, o namespace vazio será retornado.</span><span class="sxs-lookup"><span data-stu-id="25434-111">If no default namespace is specified, the empty namespace is returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="25434-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="25434-112">Return Value</span></span>  
 <span data-ttu-id="25434-113">O <xref:System.Xml.Linq.XNamespace>objeto que corresponde ao prefixo do namespace XML.</xref:System.Xml.Linq.XNamespace></span><span class="sxs-lookup"><span data-stu-id="25434-113">The <xref:System.Xml.Linq.XNamespace> object that corresponds to the XML namespace prefix.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="25434-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="25434-114">Remarks</span></span>  
 <span data-ttu-id="25434-115">O `GetXmlNamespace` operador obtém o <xref:System.Xml.Linq.XNamespace>objeto que corresponde ao prefixo do namespace XML `xmlNamespacePrefix`.</xref:System.Xml.Linq.XNamespace></span><span class="sxs-lookup"><span data-stu-id="25434-115">The `GetXmlNamespace` operator gets the <xref:System.Xml.Linq.XNamespace> object that corresponds to the XML namespace prefix `xmlNamespacePrefix`.</span></span>  
  
 <span data-ttu-id="25434-116">Você pode usar prefixos de namespace XML diretamente em literais XML e propriedades de eixo XML.</span><span class="sxs-lookup"><span data-stu-id="25434-116">You can use XML namespace prefixes directly in XML literals and XML axis properties.</span></span> <span data-ttu-id="25434-117">No entanto, você deve usar o `GetXmlNamespace` operador para converter um prefixo de namespace para um <xref:System.Xml.Linq.XNamespace>objeto antes que você pode usá-lo em seu código.</xref:System.Xml.Linq.XNamespace></span><span class="sxs-lookup"><span data-stu-id="25434-117">However, you must use the `GetXmlNamespace` operator to convert a namespace prefix to an <xref:System.Xml.Linq.XNamespace> object before you can use it in your code.</span></span> <span data-ttu-id="25434-118">Você pode acrescentar um nome de elemento não qualificados para uma <xref:System.Xml.Linq.XNamespace>objeto para obter um totalmente qualificado <xref:System.Xml.Linq.XName>do objeto, que muitos [!INCLUDE[sqltecxlinq](../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] métodos requerem.</xref:System.Xml.Linq.XName> </xref:System.Xml.Linq.XNamespace></span><span class="sxs-lookup"><span data-stu-id="25434-118">You can append an unqualified element name to an <xref:System.Xml.Linq.XNamespace> object to get a fully qualified <xref:System.Xml.Linq.XName> object, which many [!INCLUDE[sqltecxlinq](../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] methods require.</span></span>  
  
## <a name="example"></a><span data-ttu-id="25434-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="25434-119">Example</span></span>  
 <span data-ttu-id="25434-120">O exemplo a seguir importa `ns` como um prefixo de namespace XML.</span><span class="sxs-lookup"><span data-stu-id="25434-120">The following example imports `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="25434-121">Ele usa o prefixo de namespace para criar um literal XML e acessar o primeiro nó filho que tem o nome qualificado `ns:phone`.</span><span class="sxs-lookup"><span data-stu-id="25434-121">It then uses the prefix of the namespace to create an XML literal and access the first child node that has the qualified name `ns:phone`.</span></span> <span data-ttu-id="25434-122">Ele passa esse nó filho para o `ShowName` sub-rotina, que constrói um nome qualificado usando o `GetXmlNamespace` operador.</span><span class="sxs-lookup"><span data-stu-id="25434-122">It then passes that child node to the `ShowName` subroutine, which constructs a qualified name by using the `GetXmlNamespace` operator.</span></span> <span data-ttu-id="25434-123">O `ShowName` sub-rotina, em seguida, passa o nome qualificado para o <xref:System.Xml.Linq.XNode.Ancestors%2A>método para obter o pai `ns:contact` nó.</xref:System.Xml.Linq.XNode.Ancestors%2A></span><span class="sxs-lookup"><span data-stu-id="25434-123">The `ShowName` subroutine then passes the qualified name to the <xref:System.Xml.Linq.XNode.Ancestors%2A> method to get the parent `ns:contact` node.</span></span>  
  
 <span data-ttu-id="25434-124">[!code-vb[VbXMLSamples&38;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/getxmlnamespace-operator_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="25434-124">[!code-vb[VbXMLSamples#38](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/getxmlnamespace-operator_1.vb)]</span></span>  
  
 <span data-ttu-id="25434-125">Quando você chama `TestGetXmlNamespace.RunSample()`, ele exibe uma caixa de mensagem que contém o seguinte texto:</span><span class="sxs-lookup"><span data-stu-id="25434-125">When you call `TestGetXmlNamespace.RunSample()`, it displays a message box that contains the following text:</span></span>  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="25434-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="25434-126">See Also</span></span>  
 <span data-ttu-id="25434-127">[Instrução Imports (Namespace XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md) </span><span class="sxs-lookup"><span data-stu-id="25434-127">[Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md) </span></span>  
<span data-ttu-id="25434-128"> [Acessando XML no Visual Basic](../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)</span><span class="sxs-lookup"><span data-stu-id="25434-128"> [Accessing XML in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)</span></span>
