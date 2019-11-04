---
title: Atributo x:Shared
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], x:Shared attribute
- x:Shared attribute [XAML Services]
- Shared attribute in XAML [XAML Services]
ms.assetid: c8cff434-2785-405f-9f95-16deb34c9e64
ms.openlocfilehash: c820a9b1d9708e24b1460378199a6addc1e20899
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459931"
---
# <a name="xshared-attribute"></a>Atributo x:Shared
Quando definido como `false`, o modifica o comportamento de recuperação de recursos do WPF para que as solicitações para o recurso atribuído criem uma nova instância para cada solicitação, em vez de compartilhar a mesma instância para todas as solicitações.  
  
## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML  
  
```xaml  
<ResourceDictionary>  
  <object x:Shared="false".../>  
</ResourceDictionary>  
```  
  
## <a name="remarks"></a>Comentários  
 `x:Shared` é mapeado para o namespace XAML da linguagem XAML e é reconhecido como um elemento de linguagem XAML válido por .NET Framework serviços XAML e seus leitores XAML. No entanto, os recursos declarados de `x:Shared` só são relevantes para aplicativos do WPF e para o analisador XAML do WPF. No WPF, `x:Shared` só é útil como um atributo quando aplicado a um objeto que existe em um <xref:System.Windows.ResourceDictionary>do WPF. Outros usos não geram exceções de análise ou outros erros, mas não têm nenhum efeito.  
  
 O significado de `x:Shared` não é especificado na especificação da linguagem XAML. Outras implementações de XAML, como as que se baseiam em .NET Framework serviços XAML, não necessariamente fornecem suporte ao compartilhamento de recursos. Essas implementações de XAML poderiam fornecer comportamento semelhante na estrutura de suporte que também usava valores de `x:Shared`.  
  
 No WPF, a condição de `x:Shared` padrão para recursos é `true`. Essa condição significa que qualquer solicitação de recurso fornecida sempre retorna a mesma instância.  
  
 Modificar um objeto retornado por meio de uma API de recurso, como <xref:System.Windows.FrameworkElement.FindResource%2A>ou modificar um objeto diretamente em um <xref:System.Windows.ResourceDictionary>, altera o recurso original. Se as referências a esse recurso fossem referências dinâmicas a recursos, os consumidores desse recurso obterão o recurso alterado.  
  
 Se as referências ao recurso forem referências a recursos estáticos, as alterações no recurso após [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] tempo de processamento serão irrelevantes. Para obter mais informações sobre referências de recursos estáticos versus dinâmicos, consulte [recursos XAML](../../desktop-wpf/fundamentals/xaml-resources-define.md).  
  
 Especificar explicitamente `x:Shared="true"` raramente é feito, pois esse já é o padrão. Não há nenhum equivalente direto de código para `x:Shared` no modelo de objeto do WPF; Ele só pode ser especificado em um uso XAML e deve ser processado pelo comportamento padrão do WPF ou em um fluxo de nó XAML intermediário no caminho de carga, se processado usando .NET Framework serviços XAML e seus leitores XAML.  
  
 Um cenário para `x:Shared="false"` é se você definir um <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement> classe derivada como um recurso e, em seguida, introduzir o recurso de elemento em um modelo de conteúdo. `x:Shared="false"` permite que um recurso de elemento seja introduzido várias vezes na mesma coleção (como um <xref:System.Windows.Controls.UIElementCollection>). Sem `x:Shared="false"` isso é inválido porque a coleção impõe a exclusividade de seu conteúdo. No entanto, o comportamento de `x:Shared="false"` cria outra instância idêntica do recurso em vez de retornar a mesma instância.  
  
 Outro cenário para `x:Shared="false"` é se você usar um recurso de <xref:System.Windows.Freezable> para valores de animação, mas quiser modificar o recurso em uma base por animação.  
  
 A manipulação de cadeia de caracteres de `false` não diferencia maiúsculas de minúsculas.  
  
 No WPF, `x:Shared` só é válida nas seguintes condições:  
  
- O <xref:System.Windows.ResourceDictionary> que contém os itens com `x:Shared` deve ser compilado. O <xref:System.Windows.ResourceDictionary> não pode estar dentro de um XAML flexível ou usado para temas.  
  
- O <xref:System.Windows.ResourceDictionary> que contém os itens não deve ser aninhado dentro de outro <xref:System.Windows.ResourceDictionary>. Por exemplo, você não pode usar `x:Shared` para itens em um <xref:System.Windows.ResourceDictionary> que esteja dentro de um <xref:System.Windows.Style> que já é um item <xref:System.Windows.ResourceDictionary>.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.ResourceDictionary>
- [Recursos XAML](../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [Elementos base](../wpf/advanced/base-elements.md)
