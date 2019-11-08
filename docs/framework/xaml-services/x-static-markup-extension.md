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
ms.openlocfilehash: bf94f1d61ee3080c9d3582e55e0695b269801c80
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73733364"
---
# <a name="xstatic-markup-extension"></a>Extensão de marcação x:Static
Faz referência a qualquer entidade de código de valor estático definida em uma maneira compatível com Common Language Specification (CLS). A propriedade estática que é referenciada pode ser usada para fornecer o valor de uma propriedade em XAML.  
  
## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML  
  
```xaml  
<object property="{x:Static prefix:typeName.staticMemberName}" .../>  
```  
  
## <a name="xaml-values"></a>Valores XAML  
  
| | |  
|-|-|  
|`prefix`|Opcional. Um prefixo que se refere a um namespace XAML mapeado e não padrão. `prefix` é mostrado explicitamente no uso porque você raramente referencia propriedades estáticas que vêm de um namespace XAML padrão. Consulte Observações.|  
|`typeName`|Necessário. O nome do tipo que define o membro estático desejado.|  
|`staticMemberName`|Necessário. O nome do membro de valor estático desejado (uma constante, uma propriedade estática, um campo ou um valor de enumeração).|  
  
## <a name="remarks"></a>Comentários  

A entidade de código que é referenciada deve ser uma das seguintes:  
  
- Uma constante  
- Uma propriedade estática  
- Um campo  
- Um valor de enumeração

Especificar qualquer outra entidade de código, como uma propriedade não estática, causará um erro em tempo de compilação se o XAML for uma marcação compilada ou uma exceção de análise de tempo de carga XAML.  

Você pode fazer referências `x:Static` a campos estáticos ou propriedades que não estão no namespace XAML padrão para o documento XAML atual; no entanto, isso requer um mapeamento de prefixo. Os namespaces XAML quase sempre são definidos no elemento raiz do documento XAML.  

As operações de pesquisa para propriedades estáticas podem ser executadas por .NET Framework serviços XAML e seus leitores XAML e gravadores XAML, quando estão em execução com o contexto de esquema XAML padrão. Este contexto de esquema XAML pode usar a reflexão do CLR para fornecer os valores estáticos necessários para a construção do grafo de objeto. O `typeName` especificado é, na verdade, um nome de tipo XAML, não um nome de tipo CLR, embora eles sejam essencialmente o mesmo nome ao usar o contexto de esquema XAML padrão ou ao usar todas as estruturas de implementação XAML existentes baseadas em CLR.  

Tenha cuidado ao fazer referências `x:Static` que não são diretamente o tipo de valor de uma propriedade. Na sequência de processamento XAML, os valores fornecidos de uma extensão de marcação não invocam a conversão de valor adicional. Isso é verdadeiro mesmo que sua referência de `x:Static` crie uma cadeia de texto, e uma conversão de valor para valores de atributo com base na cadeia de texto normalmente ocorrerá para esse membro específico ou para qualquer valor de membro do tipo de retorno.  

A sintaxe de atributo é a sintaxe mais comum usada com essa extensão de marcação. O token da cadeia de caracteres fornecido após a cadeia de caracteres identificadora `x:Static` é atribuído como o valor <xref:System.Windows.Markup.StaticExtension.Member%2A> da classe de extensão subjacente <xref:System.Windows.Markup.StaticExtension>.  

Há dois outros usos de XAML que são tecnicamente possíveis. No entanto, esses usos são menos comuns porque são desnecessariamente detalhados:  

1. Sintaxe do elemento Object.

    ```xaml
    <x:Static Member="prefix:typeName.staticMemberName" ... />
    ```

2. Sintaxe de atributo com propriedade de membro explícita para cadeia de inicialização.

    ```xaml
    <object property="{x:Static Member=prefix:typeName.staticMemberName}" ... />
    ```

Na implementação de serviços XAML .NET Framework, o tratamento para essa extensão de marcação é definido pela classe <xref:System.Windows.Markup.StaticExtension>.  

`x:Static` é uma extensão da marcação. Todas as extensões de marcação em XAML usam os caracteres `{` e `}` em sua sintaxe de atributo, que é a Convenção pela qual um processador XAML reconhece que uma extensão de marcação deve fornecer um valor. Para obter mais informações sobre extensões de marcação, consulte [Markup Extensions for XAML Overview](markup-extensions-for-xaml-overview.md).  
  
## <a name="wpf-usage-notes"></a>Observações de uso do WPF  
 O namespace XAML padrão que você usa para a programação do WPF não contém muitas propriedades estáticas úteis, e a maioria das propriedades estáticas úteis têm suporte como conversores de tipo que facilitam o uso sem a necessidade de `{x:Static}`. Para propriedades estáticas, você deve mapear um prefixo para um namespace XAML se uma das seguintes opções for verdadeira:  
  
- Você está fazendo referência a um tipo que existe no WPF, mas que não faz parte do namespace XAML padrão para WPF (`http://schemas.microsoft.com/winfx/2006/xaml/presentation`). Esse é um cenário bastante comum para usar `x:Static`. Por exemplo, você pode usar uma referência de `x:Static` com um mapeamento de namespace XAML para o namespace <xref:System> CLR e o assembly mscorlib para fazer referência às propriedades estáticas da classe <xref:System.Environment>.  
  
- Você está fazendo referência a um tipo de um assembly personalizado.  
  
- Você está fazendo referência a um tipo que existe em um assembly do WPF, mas esse tipo está dentro de um namespace CLR que não foi mapeado para fazer parte do namespace XAML padrão do WPF. O mapeamento de namespaces CLR para o namespace XAML padrão do WPF é executado por definições nos vários assemblies do WPF (para obter mais informações sobre esse conceito, consulte [namespaces XAML e mapeamento de namespace para WPF XAML](../wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)). Os namespaces CLR não mapeados podem existir se o namespace CLR é composto principalmente de definições de classe que normalmente não são pretendidas para XAML, como <xref:System.Windows.Threading>.  
  
 Para obter mais informações sobre como usar prefixos e namespaces XAML para WPF, consulte [namespaces XAML e mapeamento de namespace para WPF XAML](../wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
## <a name="see-also"></a>Consulte também

- [Extensão de marcação x:Type](x-type-markup-extension.md)
- [Tipos migrados do WPF para System.Xaml](types-migrated-from-wpf-to-system-xaml.md)
