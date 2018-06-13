---
title: Extensão de marcação x:Static
ms.date: 03/30/2017
f1_keywords:
- StaticExtension
- xStatic
- x:Static
helpviewer_keywords:
- x:Static markup extension [XAML Services]
- Static markup extension in XAML [XAML Services]
- XAML [XAML Services], x:Static markup extension
ms.assetid: 056aee79-7cdd-434f-8174-dfc856cad343
ms.openlocfilehash: 980bf6a1bdb19afd5c8d3c798d31037ab8cd7086
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33565568"
---
# <a name="xstatic-markup-extension"></a>Extensão de marcação x:Static
Faz referência a qualquer entidade de código estático por-valor que é definida em um [!INCLUDE[TLA#tla_cls](../../../includes/tlasharptla-cls-md.md)]– compatível. A propriedade estática que é referenciada pode ser usada para fornecer o valor de uma propriedade em XAML.  
  
## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML  
  
```xaml  
<object property="{x:Static prefix:typeName.staticMemberName}" .../>  
```  
  
## <a name="xaml-values"></a>Valores XAML  
  
|||  
|-|-|  
|`prefix`|Opcional. Um prefixo que se refere a um namespace XAML mapeado, não padrão. `prefix` é mostrado explicitamente no uso de como você raramente fazem referência a propriedades estáticas que vêm de um namespace XAML padrão. Consulte Observações.|  
|`typeName`|Necessário. O nome do tipo que define o membro estático desejado.|  
|`staticMemberName`|Necessário. O nome do membro desejado de valor estático (uma constante, uma propriedade estática, um campo ou um valor de enumeração).|  
  
## <a name="remarks"></a>Comentários  
 A entidade de código referenciada deve ser um dos seguintes:  
  
-   Uma constante  
  
-   Uma propriedade estática  
  
-   Um campo  
  
-   Um valor de enumeração  
  
 Especificar qualquer outra entidade de código, como uma propriedade não estática, causa um erro de tempo de compilação se XAML é compilada com marcação ou uma exceção de análise de tempo de carregamento do XAML.  
  
 Você pode fazer `x:Static` referências a campos estáticos ou propriedades que não estão no namespace XAML padrão para o documento XAML atual; no entanto, isso requer um prefixo de mapeamento. Namespaces XAML quase sempre são definidos no elemento raiz do documento XAML.  
  
 As operações de pesquisa para propriedades estáticas podem ser executadas por serviços XAML do .NET Framework e seus leitores XAML e gravadores XAML, quando estão sendo executados com o contexto do esquema XAML padrão. Neste contexto de esquema XAML pode usar reflexão CLR para fornecer os valores estáticos necessários para a construção do gráfico de objeto. O `typeName` você especificar é realmente um tipo nome XAML, não um nome de tipo CLR, embora esses são essencialmente o mesmo nome, ao usar o contexto do esquema padrão XAML ou ao usar todas as estruturas existentes com base em CLR XAML implementa.  
  
 Tenha cuidado ao fazer `x:Static` referências que não são diretamente o tipo de valor da propriedade. No XAML o processamento de sequência, os valores de uma extensão de marcação fornecida não chamar conversão do valor adicional. Isso é verdadeiro mesmo se seu `x:Static` referência cria uma cadeia de caracteres de texto e uma conversão de valor para valores de atributo com base na cadeia de caracteres de texto geralmente ocorre para esse membro específico ou para quaisquer valores de membro do tipo de retorno.  
  
 A sintaxe de atributo é a sintaxe mais comum usada com essa extensão de marcação. O token da cadeia de caracteres fornecido após a cadeia de caracteres identificadora `x:Static` é atribuído como o valor <xref:System.Windows.Markup.StaticExtension.Member%2A> da classe de extensão subjacente <xref:System.Windows.Markup.StaticExtension>.  
  
 Há dois outros usos XAML são tecnicamente possíveis. No entanto, esses usos são menos comuns, porque eles são desnecessariamente detalhados:  
  
 **Sintaxe de elemento de objeto:** `<x:Static Member="` `prefix` `:` `typeName` `.` `staticMemberName` `" .../>`  
  
 **Sintaxe de atributo com a propriedade de membro explícita para a cadeia de caracteres de inicialização:** `<` `object` `` `property` `="{x:Static Member=` `prefix` `:` `typeName` `.` `staticMemberName` `}" .../>`  
  
 Na implementação de serviços XAML do .NET Framework, o tratamento para esta extensão de marcação é definida pelo <xref:System.Windows.Markup.StaticExtension> classe.  
  
 `x:Static` é uma extensão da marcação. Todas as extensões de marcação no uso XAML o `{` e `}` caracteres em sua sintaxe de atributo, que é a convenção pela qual um processador XAML reconhece que uma extensão de marcação deve fornecer um valor. Para obter mais informações sobre extensões de marcação, consulte [extensões de marcação para XAML Overview](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md).  
  
## <a name="wpf-usage-notes"></a>Observações de uso do WPF  
 O namespace XAML padrão você pode usar para programação de WPF não contém muitas propriedades estáticas útil e a maioria das propriedades estáticas útil tem suporte, como conversores de tipo que facilitam o uso sem a necessidade de `{x:Static}` . Para propriedades estáticas, você deve mapear um prefixo de namespace do XAML se uma das seguintes opções for verdadeira:  
  
-   Você está fazendo referência a um tipo que existe no WPF, mas não é parte do namespace para WPF XAML padrão ([!INCLUDE[TLA#tla_wpfxmlnsv1](../../../includes/tlasharptla-wpfxmlnsv1-md.md)]). Este é um cenário bastante comum para usar `x:Static`. Por exemplo, você pode usar um `x:Static` referência com um mapeamento de namespace XAML para o <xref:System> assembly de mscorlib e de namespace CLR para fazer referência as propriedades estáticas do <xref:System.Environment> classe.  
  
-   Você está fazendo referência a um tipo de um assembly personalizado.  
  
-   Você está fazendo referência de um tipo que existe em um assembly do WPF, mas esse tipo está dentro de um namespace CLR que não foi mapeado para ser parte do namespace XAML WPF padrão. O mapeamento de namespaces CLR no namespace padrão XAML WPF é executado pelo definições em vários assemblies WPF (para obter mais informações sobre esse conceito, consulte [Namespaces XAML e o mapeamento de Namespace para WPF XAML](../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)). Namespaces CLR mapeado não pode existir se namespace CLR é composta principalmente de definições de classe não são geralmente destinadas para XAML, como <xref:System.Windows.Threading>.  
  
 Para obter mais informações sobre como usar prefixos e namespaces XAML para WPF, consulte [Namespaces XAML e o mapeamento de Namespace para WPF XAML](../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
## <a name="see-also"></a>Consulte também  
 [Extensão de marcação x:Type](../../../docs/framework/xaml-services/x-type-markup-extension.md)  
 [Tipos migrados do WPF para System.Xaml](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md)
