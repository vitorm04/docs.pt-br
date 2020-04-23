---
title: Atributo x:Shared
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], x:Shared attribute
- x:Shared attribute [XAML Services]
- Shared attribute in XAML [XAML Services]
ms.assetid: c8cff434-2785-405f-9f95-16deb34c9e64
ms.openlocfilehash: e1cd1d9db5c19decd840b433f986e0ba53557a8b
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071370"
---
# <a name="xshared-attribute"></a>Atributo x:Shared

Quando definido `false`para , modifica o comportamento de recuperação de recursos do WPF para que as solicitações para o recurso atribuído criem uma nova instância para cada solicitação em vez de compartilhar a mesma instância para todas as solicitações.

## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML

```xaml
<ResourceDictionary>
  <object x:Shared="false".../>
</ResourceDictionary>
```

## <a name="remarks"></a>Comentários

`x:Shared`é mapeado para o espaço de nome XAML da linguagem XAML e é reconhecido como um elemento de linguagem XAML válido pela .NET XAML Services e seus leitores XAML. No entanto, as `x:Shared` capacidades declaradas de são apenas relevantes para aplicações WPF e para o analisador WPF XAML. No WPF, `x:Shared` só é útil como um atributo quando é aplicado <xref:System.Windows.ResourceDictionary>a um objeto que existe dentro de um WPF . Outros usos não jogam exceções de análise ou outros erros, mas não têm efeito.

O significado `x:Shared` de não está especificado na especificação do idioma XAML. Outras implementações xaml, como as que se baseiam em Serviços XAML .NET, não necessariamente fornecem suporte de compartilhamento de recursos. Tais implementações XAML poderiam fornecer comportamento semelhante `x:Shared` no quadro de suporte que também usou valores.

No WPF, `x:Shared` a condição `true`padrão para os recursos é . Essa condição significa que qualquer solicitação de recurso sempre retorna a mesma instância.

Modificar um objeto que é retornado através de <xref:System.Windows.FrameworkElement.FindResource%2A>uma API de recurso, como , ou modificar um objeto diretamente dentro de um <xref:System.Windows.ResourceDictionary>, altera o recurso original. Se as referências a esse recurso eram referências dinâmicas de recursos, os consumidores desse recurso recebem o recurso alterado.

Se as referências ao recurso foram referências estáticas de recursos, as alterações no recurso após [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] o tempo de processamento são irrelevantes. Para obter mais informações sobre referências estáticas versus dinâmicas de recursos, consulte [XAML Resources](../fundamentals/xaml-resources-define.md).

Especificar `x:Shared="true"` explicitamente raramente é feito, porque esse já é o padrão. Não há equivalente de `x:Shared` código direto para no modelo de objeto WPF; ele só pode ser especificado em um uso XAML e deve ser processado pelo comportamento padrão do WPF ou em um fluxo de nó XAML intermediário no caminho de carga se processado usando .NET XAML Services e seus leitores XAML.

Um cenário `x:Shared="false"` para é <xref:System.Windows.FrameworkElement> se <xref:System.Windows.FrameworkContentElement> você definir uma classe ou derivado como um recurso e, em seguida, você introduzir o recurso de elemento em um modelo de conteúdo. `x:Shared="false"`permite que um recurso de elemento seja introduzido várias vezes na mesma coleção (como a <xref:System.Windows.Controls.UIElementCollection>). Sem `x:Shared="false"` isso é inválido porque a coleção impõe a singularidade de seu conteúdo. No entanto, o `x:Shared="false"` comportamento cria outra instância idêntica do recurso em vez de retornar a mesma instância.

Outro cenário `x:Shared="false"` para é <xref:System.Windows.Freezable> se você usar um recurso para valores de animação, mas quiser modificar o recurso em uma base de animação.

O manuseio de `false` cordas não é sensível ao caso.

No WPF, `x:Shared` só é válido sob as seguintes condições:

- O <xref:System.Windows.ResourceDictionary> que contém os `x:Shared` itens com deve ser compilado. O <xref:System.Windows.ResourceDictionary> não pode estar dentro de XAML solto ou usado para temas.

- O <xref:System.Windows.ResourceDictionary> que contém os itens não deve <xref:System.Windows.ResourceDictionary>ser aninhado dentro de outro . Por exemplo, você `x:Shared` não pode usar <xref:System.Windows.ResourceDictionary> para itens <xref:System.Windows.Style> em um <xref:System.Windows.ResourceDictionary> que está dentro de um que já é um item.

## <a name="see-also"></a>Confira também

- <xref:System.Windows.ResourceDictionary>
- [Recursos XAML](../fundamentals/xaml-resources-define.md)
- [Elementos base](../../framework/wpf/advanced/base-elements.md)
