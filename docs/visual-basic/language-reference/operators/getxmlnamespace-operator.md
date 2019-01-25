---
title: Operador GetXmlNamespace (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.GetXmlNamespace
- GetXmlNamespace
helpviewer_keywords:
- GetXmlNamespace operator [Visual Basic]
- GetXmlNamespace keyword [Visual Basic]
ms.assetid: d0d28cfd-0755-4896-ae0b-4981aa35517c
ms.openlocfilehash: f9201aa4b2aa9280b9b3a4e0a2badf25ea819088
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54684743"
---
# <a name="getxmlnamespace-operator-visual-basic"></a><span data-ttu-id="57e78-102">Operador GetXmlNamespace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="57e78-102">GetXmlNamespace Operator (Visual Basic)</span></span>
<span data-ttu-id="57e78-103">Obtém o <xref:System.Xml.Linq.XNamespace> objeto que corresponde ao prefixo de namespace XML especificado.</span><span class="sxs-lookup"><span data-stu-id="57e78-103">Gets the <xref:System.Xml.Linq.XNamespace> object that corresponds to the specified XML namespace prefix.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57e78-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="57e78-104">Syntax</span></span>  
  
```  
GetXmlNamespace(xmlNamespacePrefix)  
```  
  
## <a name="parts"></a><span data-ttu-id="57e78-105">Partes</span><span class="sxs-lookup"><span data-stu-id="57e78-105">Parts</span></span>  
 `xmlNamespacePrefix`  
 <span data-ttu-id="57e78-106">Opcional.</span><span class="sxs-lookup"><span data-stu-id="57e78-106">Optional.</span></span> <span data-ttu-id="57e78-107">A cadeia de caracteres que identifica o prefixo de namespace XML.</span><span class="sxs-lookup"><span data-stu-id="57e78-107">The string that identifies the XML namespace prefix.</span></span> <span data-ttu-id="57e78-108">Se for fornecido, essa cadeia de caracteres deve ser um identificador XML válido.</span><span class="sxs-lookup"><span data-stu-id="57e78-108">If supplied, this string must be a valid XML identifier.</span></span> <span data-ttu-id="57e78-109">Para obter mais informações, consulte [nomes de declarado elementos e atributos XML](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="57e78-109">For more information, see [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span> <span data-ttu-id="57e78-110">Se nenhum prefixo for especificado, o namespace padrão é retornado.</span><span class="sxs-lookup"><span data-stu-id="57e78-110">If no prefix is specified, the default namespace is returned.</span></span> <span data-ttu-id="57e78-111">Se nenhum namespace padrão for especificado, o namespace vazio será retornado.</span><span class="sxs-lookup"><span data-stu-id="57e78-111">If no default namespace is specified, the empty namespace is returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="57e78-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="57e78-112">Return Value</span></span>  
 <span data-ttu-id="57e78-113">O <xref:System.Xml.Linq.XNamespace> objeto que corresponde ao prefixo de namespace XML.</span><span class="sxs-lookup"><span data-stu-id="57e78-113">The <xref:System.Xml.Linq.XNamespace> object that corresponds to the XML namespace prefix.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="57e78-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="57e78-114">Remarks</span></span>  
 <span data-ttu-id="57e78-115">O `GetXmlNamespace` operador obtém o <xref:System.Xml.Linq.XNamespace> objeto que corresponde ao prefixo de namespace XML `xmlNamespacePrefix`.</span><span class="sxs-lookup"><span data-stu-id="57e78-115">The `GetXmlNamespace` operator gets the <xref:System.Xml.Linq.XNamespace> object that corresponds to the XML namespace prefix `xmlNamespacePrefix`.</span></span>  
  
 <span data-ttu-id="57e78-116">Você pode usar prefixos de namespace XML diretamente em literais XML e propriedades de eixo XML.</span><span class="sxs-lookup"><span data-stu-id="57e78-116">You can use XML namespace prefixes directly in XML literals and XML axis properties.</span></span> <span data-ttu-id="57e78-117">No entanto, você deve usar o `GetXmlNamespace` operador para converter um prefixo de namespace para um <xref:System.Xml.Linq.XNamespace> antes que você pode usá-lo em seu código do objeto.</span><span class="sxs-lookup"><span data-stu-id="57e78-117">However, you must use the `GetXmlNamespace` operator to convert a namespace prefix to an <xref:System.Xml.Linq.XNamespace> object before you can use it in your code.</span></span> <span data-ttu-id="57e78-118">Você pode acrescentar um nome de elemento não qualificado para um <xref:System.Xml.Linq.XNamespace> objeto do qual obter um totalmente qualificado <xref:System.Xml.Linq.XName> do objeto, que muitos [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] métodos exigem.</span><span class="sxs-lookup"><span data-stu-id="57e78-118">You can append an unqualified element name to an <xref:System.Xml.Linq.XNamespace> object to get a fully qualified <xref:System.Xml.Linq.XName> object, which many [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] methods require.</span></span>  
  
## <a name="example"></a><span data-ttu-id="57e78-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="57e78-119">Example</span></span>  
 <span data-ttu-id="57e78-120">O exemplo a seguir importa `ns` como um prefixo de namespace XML.</span><span class="sxs-lookup"><span data-stu-id="57e78-120">The following example imports `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="57e78-121">Ele usa o prefixo de namespace para criar um literal XML e acessar o primeiro nó filho que tem o nome qualificado `ns:phone`.</span><span class="sxs-lookup"><span data-stu-id="57e78-121">It then uses the prefix of the namespace to create an XML literal and access the first child node that has the qualified name `ns:phone`.</span></span> <span data-ttu-id="57e78-122">Ele, em seguida, passa o nó filho para o `ShowName` sub-rotina, que constrói um nome qualificado usando o `GetXmlNamespace` operador.</span><span class="sxs-lookup"><span data-stu-id="57e78-122">It then passes that child node to the `ShowName` subroutine, which constructs a qualified name by using the `GetXmlNamespace` operator.</span></span> <span data-ttu-id="57e78-123">O `ShowName` sub-rotina, em seguida, passa o nome qualificado para o <xref:System.Xml.Linq.XNode.Ancestors%2A> método para obter o pai `ns:contact` nó.</span><span class="sxs-lookup"><span data-stu-id="57e78-123">The `ShowName` subroutine then passes the qualified name to the <xref:System.Xml.Linq.XNode.Ancestors%2A> method to get the parent `ns:contact` node.</span></span>  
  
 [!code-vb[VbXMLSamples#38](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/getxmlnamespace-operator_1.vb)]  
  
 <span data-ttu-id="57e78-124">Quando você chama `TestGetXmlNamespace.RunSample()`, ele exibe uma caixa de mensagem que contém o texto a seguir:</span><span class="sxs-lookup"><span data-stu-id="57e78-124">When you call `TestGetXmlNamespace.RunSample()`, it displays a message box that contains the following text:</span></span>  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="57e78-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="57e78-125">See also</span></span>
- [<span data-ttu-id="57e78-126">Instrução Imports (Namespace de XML)</span><span class="sxs-lookup"><span data-stu-id="57e78-126">Imports Statement (XML Namespace)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
- [<span data-ttu-id="57e78-127">Acessando XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="57e78-127">Accessing XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
