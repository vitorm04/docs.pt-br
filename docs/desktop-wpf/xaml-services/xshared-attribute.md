---
title: Atributo x:Shared
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], x:Shared attribute
- x:Shared attribute [XAML Services]
- Shared attribute in XAML [XAML Services]
ms.assetid: c8cff434-2785-405f-9f95-16deb34c9e64
ms.openlocfilehash: d5000b51d83066ec2d529db2033d8ac54f7ad329
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557782"
---
# <a name="xshared-attribute"></a>Atributo x:Shared

Quando definido como `false` , modifica o comportamento de recuperação de recursos do WPF para que as solicitações para o recurso atribuído criem uma nova instância para cada solicitação em vez de compartilhar a mesma instância para todas as solicitações.

## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML

```xaml
<ResourceDictionary>
  <object x:Shared="false".../>
</ResourceDictionary>
```

## <a name="remarks"></a>Comentários

`x:Shared` é mapeado para o namespace XAML da linguagem XAML e é reconhecido como um elemento de linguagem XAML válido pelos serviços XAML .NET e seus leitores XAML. No entanto, os recursos declarados do `x:Shared` são relevantes apenas para aplicativos do WPF e para o analisador XAML do WPF. No WPF, `x:Shared` é útil apenas como um atributo quando ele é aplicado a um objeto que existe dentro de um WPF <xref:System.Windows.ResourceDictionary> . Outros usos não geram exceções de análise ou outros erros, mas não têm nenhum efeito.

O significado de `x:Shared` não é especificado na especificação da linguagem XAML. Outras implementações de XAML, como as que se baseiam nos serviços XAML .NET, não necessariamente fornecem suporte ao compartilhamento de recursos. Essas implementações de XAML poderiam fornecer um comportamento semelhante na estrutura de suporte que também usava `x:Shared` valores.

No WPF, a `x:Shared` condição padrão para recursos é `true` . Essa condição significa que qualquer solicitação de recurso fornecida sempre retorna a mesma instância.

Modificar um objeto que é retornado por meio de uma API de recurso, como <xref:System.Windows.FrameworkElement.FindResource%2A> ou modificar um objeto diretamente dentro de um <xref:System.Windows.ResourceDictionary> , altera o recurso original. Se as referências a esse recurso fossem referências dinâmicas a recursos, os consumidores desse recurso obterão o recurso alterado.

Se as referências ao recurso forem referências a recursos estáticos, as alterações no recurso após o [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] tempo de processamento serão irrelevantes. Para obter mais informações sobre referências de recursos estáticos versus dinâmicos, consulte [recursos XAML](../fundamentals/xaml-resources-define.md).

Especificar explicitamente `x:Shared="true"` é raramente feito, pois esse já é o padrão. Não há nenhum equivalente direto de código para `x:Shared` no modelo de objeto do WPF; ele só pode ser especificado em um uso XAML e deve ser processado pelo comportamento padrão do WPF ou em um fluxo de nó XAML intermediário no caminho de carga, se processado usando os serviços XAML .net e seus leitores XAML.

Um cenário para o `x:Shared="false"` é se você definir <xref:System.Windows.FrameworkElement> uma <xref:System.Windows.FrameworkContentElement> classe derivada ou como um recurso e, em seguida, introduzir o recurso de elemento em um modelo de conteúdo. `x:Shared="false"` permite que um recurso de elemento seja introduzido várias vezes na mesma coleção (como um <xref:System.Windows.Controls.UIElementCollection> ). Sem `x:Shared="false"` isso é inválido porque a coleção impõe exclusividade de seu conteúdo. No entanto, o `x:Shared="false"` comportamento cria outra instância idêntica do recurso em vez de retornar a mesma instância.

Outro cenário do `x:Shared="false"` é se você usar um <xref:System.Windows.Freezable> recurso para valores de animação, mas quiser modificar o recurso em uma base por animação.

A manipulação de cadeia de caracteres de `false` não diferencia maiúsculas de minúsculas.

No WPF, `x:Shared` só é válido nas seguintes condições:

- O <xref:System.Windows.ResourceDictionary> que contém os itens com `x:Shared` deve ser compilado. O <xref:System.Windows.ResourceDictionary> não pode estar no XAML flexível ou usado para temas.

- O <xref:System.Windows.ResourceDictionary> que contém os itens não deve ser aninhado dentro de outro <xref:System.Windows.ResourceDictionary> . Por exemplo, você não pode usar `x:Shared` para itens em um <xref:System.Windows.ResourceDictionary> que esteja dentro de um <xref:System.Windows.Style> que já seja um <xref:System.Windows.ResourceDictionary> Item.

## <a name="see-also"></a>Confira também

- <xref:System.Windows.ResourceDictionary>
- [Recursos XAML](../fundamentals/xaml-resources-define.md)
- [Elementos base](/dotnet/desktop/wpf/advanced/base-elements)
