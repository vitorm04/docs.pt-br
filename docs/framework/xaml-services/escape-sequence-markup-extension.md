---
title: '{} Extensão de marcação de - sequência de escape'
ms.date: 03/30/2017
f1_keywords:
- '{}'
helpviewer_keywords:
- XAML [XAML Services], quotation mark (")
- '{} escape sequence [XAML Services]'
- XAML [XAML Services], {} escape sequence
- XAML [XAML Services], escape sequence
- quotation mark (") [XAML Services]
- escape sequence [XAML Services]
ms.assetid: 3ce3e2ad-a868-43f9-9c98-b29561cb146e
ms.openlocfilehash: eaee0a1f92d8b7cb3810651eda21f1cc800ebf57
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2019
ms.locfileid: "58018552"
---
# <a name="-escape-sequence--markup-extension"></a><span data-ttu-id="ac5d8-102">{} Sequência de escape / extensão de marcação</span><span class="sxs-lookup"><span data-stu-id="ac5d8-102">{} Escape Sequence / Markup Extension</span></span>
<span data-ttu-id="ac5d8-103">Fornece a sequência de escape do XAML para valores de atributo.</span><span class="sxs-lookup"><span data-stu-id="ac5d8-103">Provides the XAML escape sequence for attribute values.</span></span> <span data-ttu-id="ac5d8-104">A sequência de escape permite que os valores subsequentes no atributo deve ser interpretado como um literal.</span><span class="sxs-lookup"><span data-stu-id="ac5d8-104">The escape sequence allows the subsequent values in the attribute to be interpreted as a literal.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="ac5d8-105">Uso do Atributo XAML</span><span class="sxs-lookup"><span data-stu-id="ac5d8-105">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{} literalValue" .../>  
```  
  
## <a name="xaml-property-element-usage"></a><span data-ttu-id="ac5d8-106">Uso do elemento propriedade XAML</span><span class="sxs-lookup"><span data-stu-id="ac5d8-106">XAML Property Element Usage</span></span>  
  
```  
<object>  
  <object.property>  
    {} literalValue  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="ac5d8-107">Valores XAML</span><span class="sxs-lookup"><span data-stu-id="ac5d8-107">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ac5d8-108">*literalValue*</span><span class="sxs-lookup"><span data-stu-id="ac5d8-108">*literalValue*</span></span>|<span data-ttu-id="ac5d8-109">A cadeia de caracteres literal que segue a sequência de escape.</span><span class="sxs-lookup"><span data-stu-id="ac5d8-109">The literal string that follows the escape sequence.</span></span> <span data-ttu-id="ac5d8-110">Normalmente, essa cadeia de caracteres contém uma chave de abertura ou fechamento ({ou}).</span><span class="sxs-lookup"><span data-stu-id="ac5d8-110">Typically this string contains an open or close brace ({ or }).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ac5d8-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="ac5d8-111">Remarks</span></span>  
 <span data-ttu-id="ac5d8-112">A sequência de escape ({}) é usado para que uma chave de abertura ({}) pode ser usada como um caractere literal em XAML.</span><span class="sxs-lookup"><span data-stu-id="ac5d8-112">The escape sequence ({}) is used so that an open brace ({)can be used as a literal character in XAML.</span></span>  
  
 <span data-ttu-id="ac5d8-113">Leitores XAML normalmente usam a chave de abertura ({}) para indicar o ponto de entrada de uma extensão de marcação; no entanto, eles primeiro verificam o próximo caractere para determinar se ele é uma chave de fechamento (}).</span><span class="sxs-lookup"><span data-stu-id="ac5d8-113">XAML readers typically use the open brace ({) to denote the entry point of a markup extension; however, they first check the next character to determine whether it is a closing brace (}).</span></span> <span data-ttu-id="ac5d8-114">Somente quando as duas chaves ({}) são adjacente, serão consideradas uma sequência de escape.</span><span class="sxs-lookup"><span data-stu-id="ac5d8-114">Only when the two braces ({}) are adjacent, are they considered an escape sequence.</span></span>  
  
 <span data-ttu-id="ac5d8-115">Se a sequência de escape for encontrada, o leitor XAML deve processar o restante da cadeia de caracteres como uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="ac5d8-115">If the escape sequence is encountered, the XAML reader should process the remainder of the string as a string.</span></span> <span data-ttu-id="ac5d8-116">No entanto, se a sequência de escape for aplicada a um membro que tem um conversor de tipo, a cadeia de caracteres pode passar por conversão de tipo quando ele é interpretado por um gravador XAML.</span><span class="sxs-lookup"><span data-stu-id="ac5d8-116">However, if the escape sequence is applied to a member that has a type converter, the string might undergo type conversion when it is interpreted by a XAML writer.</span></span>  
  
 <span data-ttu-id="ac5d8-117">A sequência de escape não é uma extensão de marcação e não é apoiada por uma classe.</span><span class="sxs-lookup"><span data-stu-id="ac5d8-117">The escape sequence is not a markup extension and is not backed by a class.</span></span> <span data-ttu-id="ac5d8-118">No entanto, é uma convenção que os leitores XAML (incluindo os leitores XAML personalizados) devem respeitar.</span><span class="sxs-lookup"><span data-stu-id="ac5d8-118">However, it is a convention that XAML readers (including custom XAML readers) should respect.</span></span>  
  
 <span data-ttu-id="ac5d8-119">Uma marca de aspas (") não pode ser usada como uma sequência de escape dessa maneira.</span><span class="sxs-lookup"><span data-stu-id="ac5d8-119">A quotation mark (") cannot be used as an escape sequence in this manner.</span></span> <span data-ttu-id="ac5d8-120">Se você precisar definir uma marca de aspas simples como um valor de propriedade para uma propriedade não-conteúdo, usar a sintaxe de elemento de propriedade e colocar a marca de aspas como uma cadeia de caracteres dentro do elemento de propriedade ou usar uma entidade de caractere XML.</span><span class="sxs-lookup"><span data-stu-id="ac5d8-120">If you need to set a quotation mark as a property value for a noncontent property, use property element syntax and place the quotation mark as a string inside the property element, or use an XML character entity.</span></span> <span data-ttu-id="ac5d8-121">Para uma propriedade de conteúdo, as aspas podem ser todo o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="ac5d8-121">For a content property, the quotation mark can be the entire content.</span></span>  
  
 <span data-ttu-id="ac5d8-122">A sequência de escape ({}) é frequentemente necessário ao especificar um tipo XML que deve incluir um qualificador de namespace em um local em que uma extensão de marcação XAML pode aparecer.</span><span class="sxs-lookup"><span data-stu-id="ac5d8-122">The escape sequence ({}) is frequently required when specifying an XML type that must include a namespace qualifier in a location where a XAML markup extension might appear.</span></span> <span data-ttu-id="ac5d8-123">Isso inclui o início de um valor de atributo XAML e, em uma extensão de marcação, imediatamente após o sinal de igual (=).</span><span class="sxs-lookup"><span data-stu-id="ac5d8-123">This includes the start of a XAML attribute value, and in a markup extension, immediately after an equal sign (=).</span></span> <span data-ttu-id="ac5d8-124">O exemplo a seguir mostra as sequências de escape para um namespace XML que aparece no início de um valor de atributo XAML.</span><span class="sxs-lookup"><span data-stu-id="ac5d8-124">The following example shows escape sequences for an XML namespace that appears at the start of a XAML attribute value.</span></span>  
  
 [!code-xaml[XLINQExample#StackPanelResources](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]  
  
## <a name="see-also"></a><span data-ttu-id="ac5d8-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ac5d8-125">See also</span></span>
- [<span data-ttu-id="ac5d8-126">Conversores de tipo e extensões de marcação para XAML</span><span class="sxs-lookup"><span data-stu-id="ac5d8-126">Type Converters and Markup Extensions for XAML</span></span>](type-converters-and-markup-extensions-for-xaml.md)
- [<span data-ttu-id="ac5d8-127">Entidades e XAML de caractere XML</span><span class="sxs-lookup"><span data-stu-id="ac5d8-127">XML Character Entities and XAML</span></span>](xml-character-entities-and-xaml.md)
