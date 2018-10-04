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
ms.openlocfilehash: 8a14b00fe762d325028072cd0ea3eecf9b9206e3
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48780278"
---
# <a name="xstatic-markup-extension"></a>Extensão de marcação x:Static
Faz referência a qualquer entidade de código estático por-valor que é definida em um [!INCLUDE[TLA#tla_cls](../../../includes/tlasharptla-cls-md.md)]– maneira em conformidade. A propriedade estática que é referenciada pode ser usada para fornecer o valor de uma propriedade em XAML.  
  
## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML  
  
```xaml  
<object property="{x:Static prefix:typeName.staticMemberName}" .../>  
```  
  
## <a name="xaml-values"></a>Valores XAML  
  
| | |  
|-|-|  
|`prefix`|Opcional. Um prefixo que se refere a um namespace XAML mapeado, não-padrão. `prefix` é mostrado explicitamente o uso em porque você raramente fazem referência a propriedades estáticas que vêm de um namespace XAML padrão. Consulte Observações.|  
|`typeName`|Necessário. O nome do tipo que define o membro estático desejado.|  
|`staticMemberName`|Necessário. O nome do membro desejado de valor estático (uma constante, uma propriedade estática, um campo ou um valor de enumeração).|  
  
## <a name="remarks"></a>Comentários  

A entidade de código que é referenciada deve ser um destes procedimentos:  
  
-   Uma constante  
-   Uma propriedade estática  
-   Um campo  
-   Um valor de enumeração

Especificar qualquer outra entidade de código, como uma propriedade não estática, causa um erro de tempo de compilação se o XAML é compilada com marcação, ou uma exceção de análise de tempo de carregamento XAML.  

Você pode fazer `x:Static` referências a campos estáticos ou propriedades que não estão no namespace XAML padrão para o documento atual do XAML; no entanto, isso requer um prefixo de mapeamento. Namespaces XAML quase sempre são definidos no elemento raiz do documento XAML.  

As operações de pesquisa para propriedades estáticas podem ser executadas por serviços XAML do .NET Framework e seus leitores XAML e gravadores XAML, quando eles estiverem em execução com o contexto do esquema XAML padrão. Neste contexto de esquema XAML pode usar a reflexão do CLR para fornecer os valores estáticos necessários para a construção do grafo de objeto. O `typeName` você especificar é realmente um XAML nome de tipo, não um nome de tipo CLR, embora essas sejam essencialmente o mesmo nome, ao usar o contexto de esquema XAML padrão ou ao usar todas as estruturas existentes baseados em CLR XAML-implementando.  

Tenha cuidado ao fazer `x:Static` referências que não são diretamente o tipo de valor da propriedade. No XAML o processamento de sequência de valores de uma extensão de marcação fornecida não invocar conversão do valor adicional. Isso é verdadeiro mesmo se seu `x:Static` referência cria uma cadeia de caracteres de texto, e uma conversão de valor para valores de atributo com base na cadeia de caracteres de texto normalmente ocorre para que o membro específico ou para quaisquer valores de membro do tipo de retorno.  

A sintaxe de atributo é a sintaxe mais comum usada com essa extensão de marcação. O token da cadeia de caracteres fornecido após a cadeia de caracteres identificadora `x:Static` é atribuído como o valor <xref:System.Windows.Markup.StaticExtension.Member%2A> da classe de extensão subjacente <xref:System.Windows.Markup.StaticExtension>.  

Há dois outros usos XAML são tecnicamente possíveis. No entanto, esses usos são menos comuns, como eles são desnecessariamente detalhados:  

1.  Sintaxe de elemento de objeto.

    ```xaml
    <x:Static Member="prefix:typeName.staticMemberName" ... />
    ```

2.  Sintaxe de propriedade do membro explícita para a cadeia de caracteres de inicialização de atributo.

    ```xaml
    <object property="{x:Static Member=prefix:typeName.staticMemberName}" ... />
    ```

Na implementação de serviços de XAML do .NET Framework, o tratamento para essa extensão de marcação é definido pelo <xref:System.Windows.Markup.StaticExtension> classe.  

`x:Static` é uma extensão da marcação. Todas as extensões de marcação no uso XAML a `{` e `}` caracteres na sintaxe de atributo, que é a convenção pela qual um processador XAML reconhece que uma extensão de marcação deve fornecer um valor. Para obter mais informações sobre extensões de marcação, consulte [extensões de marcação para visão geral de XAML](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md).  
  
## <a name="wpf-usage-notes"></a>Notas de uso do WPF  
 Namespace XAML padrão, você pode usar para a programação do WPF não contém muitas propriedades estáticas úteis, e a maioria das propriedades estáticas útil tem suporte, como conversores de tipo que facilitam o uso sem a necessidade de `{x:Static}` . Para propriedades estáticas, você deve mapear um prefixo para um namespace XAML, se uma das seguintes opções for verdadeira:  
  
-   Você está fazendo referência a um tipo que existe no WPF, mas não é parte do namespace XAML padrão do WPF ([!INCLUDE[TLA#tla_wpfxmlnsv1](../../../includes/tlasharptla-wpfxmlnsv1-md.md)]). Isso é um cenário bastante comum para usar `x:Static`. Por exemplo, você pode usar um `x:Static` referência com um mapeamento de namespace XAML para o <xref:System> assembly mscorlib e namespace do CLR para fazer referência a propriedades estáticas do <xref:System.Environment> classe.  
  
-   Você está fazendo referência a um tipo de um assembly personalizado.  
  
-   Você está fazendo referência a um tipo que existe em um assembly do WPF, mas esse tipo está dentro de um namespace CLR que não foi mapeado para ser parte do namespace XAML do WPF padrão. O mapeamento de namespaces CLR dentro do namespace XAML padrão do WPF é executado pelas definições em vários assemblies WPF (para obter mais informações sobre esse conceito, consulte [Namespaces de XAML e mapeamento de Namespace para XAML WPF](../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)). Namespaces CLR não mapeado pode existir se esse namespace de CLR é composta principalmente de definições de classe não são geralmente destinadas para XAML, como <xref:System.Windows.Threading>.  
  
 Para obter mais informações sobre como usar prefixos e namespaces XAML para WPF, consulte [Namespaces XAML e mapeamento de Namespace para XAML WPF](../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
## <a name="see-also"></a>Consulte também  
 [Extensão de marcação x:Type](../../../docs/framework/xaml-services/x-type-markup-extension.md)  
 [Tipos migrados do WPF para System.Xaml](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md)
