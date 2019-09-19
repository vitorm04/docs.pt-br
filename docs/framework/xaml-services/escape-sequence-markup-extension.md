---
title: '{}Sequência de escape-extensão de marcação'
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
ms.openlocfilehash: b0646c62a1342eb160d1967e86ac286429013f3c
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053868"
---
# <a name="-escape-sequence--markup-extension"></a>{} Sequência de escape /extensão de marcação
Fornece a sequência de escape XAML para valores de atributo. A sequência de escape permite que os valores subsequentes no atributo sejam interpretados como um literal.  
  
## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML  
  
```xaml  
<object property="{} literalValue" .../>  
```  
  
## <a name="xaml-property-element-usage"></a>Uso do elemento propriedade XAML  
  
```xaml  
<object>  
  <object.property>  
    {} literalValue  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a>Valores XAML  
  
|||  
|-|-|  
|*literalValue*|A cadeia de caracteres literal que segue a sequência de escape. Normalmente, essa cadeia de caracteres contém uma chave de abertura ou fechamento ({ou}).|  
  
## <a name="remarks"></a>Comentários  
 A sequência de escape{}() é usada para que uma chave de abertura ({) possa ser usada como um caractere literal em XAML.  
  
 Os leitores XAML normalmente usam a chave de abertura ({) para denotar o ponto de entrada de uma extensão de marcação; no entanto, eles primeiro verificam o próximo caractere para determinar se ele é uma chave de fechamento (}). Somente quando as duas chaves ({}) são adjacentes, elas são consideradas uma sequência de escape.  
  
 Se a sequência de escape for encontrada, o leitor XAML deverá processar o restante da cadeia de caracteres como uma cadeia de caracteres. No entanto, se a sequência de escape for aplicada a um membro que tenha um conversor de tipo, a cadeia de caracteres poderá sofrer conversão de tipo quando for interpretada por um gravador XAML.  
  
 A sequência de escape não é uma extensão de marcação e não é apoiada por uma classe. No entanto, é uma Convenção de que os leitores XAML (incluindo leitores XAML personalizados) devem respeitar.  
  
 Uma aspa (") não pode ser usada como uma sequência de escape dessa maneira. Se você precisar definir uma aspa como um valor de propriedade para uma propriedade que não seja de conteúdo, use a sintaxe do elemento de propriedade e coloque as aspas como uma cadeia de caracteres dentro do elemento de propriedade ou use uma entidade de caractere XML. Para uma propriedade de conteúdo, a aspa pode ser todo o conteúdo.  
  
 A sequência de escape{}() é frequentemente necessária ao especificar um tipo XML que deve incluir um qualificador de namespace em um local onde uma extensão de marcação XAML pode aparecer. Isso inclui o início de um valor de atributo XAML e, em uma extensão de marcação, imediatamente após um sinal de igual (=). O exemplo a seguir mostra as sequências de escape para um namespace XML que aparece no início de um valor de atributo XAML.  
  
 [!code-xaml[XLINQExample#StackPanelResources](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]  
  
## <a name="see-also"></a>Consulte também

- [Conversores de tipo e extensões de marcação para XAML](type-converters-and-markup-extensions-for-xaml.md)
- [Entidades e XAML de caractere XML](xml-character-entities-and-xaml.md)
