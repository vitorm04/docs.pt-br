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
ms.openlocfilehash: fb9ee6807135f17fd9e0c799533bba28b369ebe2
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2020
ms.locfileid: "82072021"
---
# <a name="xstatic-markup-extension"></a>Extensão de marcação x:Static

Faz referência a qualquer entidade de código de valor estático que seja definida de forma compatível com a Especificação de Linguagem Comum (CLS). A propriedade estática que é referenciada pode ser usada para fornecer o valor de uma propriedade em XAML.

## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML

```xaml
<object property="{x:Static prefix:typeName.staticMemberName}" .../>
```

## <a name="xaml-values"></a>Valores XAML

| | |
|-|-|
|`prefix`|Opcional. Um prefixo que se refere a um espaço de nome XAML mapeado e não padrão. `prefix`é mostrado explicitamente no uso porque você raramente referencia propriedades estáticas que vêm de um namespace XAML padrão. Consulte Observações.|
|`typeName`|Obrigatórios. O nome do tipo que define o membro estático desejado.|
|`staticMemberName`|Obrigatórios. O nome do membro de valor estático desejado (uma constante, uma propriedade estática, um campo ou um valor de enumeração).|

## <a name="remarks"></a>Comentários

A entidade de código que é referenciada deve ser uma das seguintes:

- Uma constante
- Uma propriedade estática
- Um campo
- Um valor de enumeração

Especificar qualquer outra entidade de código, como uma propriedade não estática, causa um erro de tempo de compilação se o XAML for compilado ou uma exceção de análise de tempo de carga XAML.

Você pode `x:Static` fazer referências a campos estáticos ou propriedades que não estejam no namespace XAML padrão para o documento XAML atual; no entanto, isso requer um mapeamento de prefixo. Os namespaces XAML são quase sempre definidos no elemento raiz do documento XAML.

As operações de pesquisa para propriedades estáticas podem ser realizadas pela .NET XAML Services e seus leitores XAML e escritores XAML, quando estão sendo executados com o contexto padrão do esquema XAML. Este contexto de esquema XAML pode usar a reflexão CLR para fornecer os valores estáticos necessários para a construção de gráficos de objetos. O `typeName` que você especifica é na verdade um nome de tipo XAML, não um nome de tipo CLR, embora estes sejam essencialmente o mesmo nome ao usar o contexto padrão do esquema XAML ou ao usar todas as estruturas de implementação XAML baseadas em CLR existentes.

Tenha cuidado ao `x:Static` fazer referências que não são diretamente o tipo de valor de um imóvel. Na seqüência de processamento XAML, os valores fornecidos de uma extensão de marcação não invocam conversão de valor adicional. Isso é verdade `x:Static` mesmo se sua referência criar uma seqüência de texto, e uma conversão de valor para valores de atributo com base na seqüência de texto normalmente ocorre para esse membro específico ou para quaisquer valores membros do tipo de retorno.

A sintaxe de atributo é a sintaxe mais comum usada com essa extensão de marcação. O token da cadeia de caracteres fornecido após a cadeia de caracteres identificadora `x:Static` é atribuído como o valor <xref:System.Windows.Markup.StaticExtension.Member%2A> da classe de extensão subjacente <xref:System.Windows.Markup.StaticExtension>.

Existem dois outros usos XAML que são tecnicamente possíveis. No entanto, esses usos são menos comuns porque são desnecessariamente verbosos:

01. Sintaxe do elemento objeto.

    ```xaml
    <x:Static Member="prefix:typeName.staticMemberName" ... />
    ```

02. Sintaxe de atributo com propriedade membro explícita para seqüência de inicialização.

    ```xaml
    <object property="{x:Static Member=prefix:typeName.staticMemberName}" ... />
    ```

Na implementação do .NET XAML Services, o manuseio <xref:System.Windows.Markup.StaticExtension> dessa extensão de marcação é definido pela classe.

`x:Static` é uma extensão da marcação. Todas as extensões de marcação `{` `}` em XAML usam os caracteres em sua sintaxe de atributos, que é a convenção pela qual um processador XAML reconhece que uma extensão de marcação deve fornecer um valor. Para obter mais informações sobre extensões de marcação, consulte [Extensões de marcação para visão geral XAML](markup-extensions-overview.md).

## <a name="wpf-usage-notes"></a>Notas de uso do WPF

O namespace XAML padrão que você usa para programação WPF não contém muitas propriedades estáticas úteis, e `{x:Static}` a maioria das propriedades estáticas úteis têm suporte, como conversores de tipo que facilitam o uso sem necessidade . Para propriedades estáticas, você deve mapear um prefixo para um namespace XAML se um dos seguintes for verdadeiro:

- Você está fazendo referência a um tipo que existe no WPF, mas não`http://schemas.microsoft.com/winfx/2006/xaml/presentation`faz parte do namespace XAML padrão para WPF ( ). Este é um cenário bastante `x:Static`comum para o uso . Por exemplo, você `x:Static` pode usar uma referência com um <xref:System> mapeamento de namespace XAML para o namespace <xref:System.Environment> clr e o conjunto mscorlib, a fim de referenciar as propriedades estáticas da classe.

- Você está fazendo referência a um tipo de uma montagem personalizada.

- Você está fazendo referência a um tipo que existe em um conjunto WPF, mas esse tipo está dentro de um namespace CLR que não foi mapeado para fazer parte do namespace Padrão XAML do WPF. O mapeamento de namespaces CLR no namespace padrão xaml para WPF é realizado por definições nos vários conjuntos WPF (para obter mais informações sobre esse conceito, consulte [XAML Namespaces e Namespace Mapping for WPF XAML](../../framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)). Os namespaces CLR não mapeados podem existir se esse namespace CLR for composto principalmente de <xref:System.Windows.Threading>definições de classe que não são tipicamente destinadas a XAML, tais como .

Para obter mais informações sobre como usar prefixos e namespaces XAML para WPF, consulte [XAML Namespaces e Namespace Mapping for WPF XAML](../../framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).

## <a name="see-also"></a>Confira também

- [Extensão de marcação x:Type](xtype-markup-extension.md)
- [Tipos migrados do WPF para System.Xaml](../../framework/wpf/advanced/types-migrated-from-wpf-to-system.md)
