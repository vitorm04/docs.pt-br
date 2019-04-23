---
title: Atributo x:Shared
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], x:Shared attribute
- x:Shared attribute [XAML Services]
- Shared attribute in XAML [XAML Services]
ms.assetid: c8cff434-2785-405f-9f95-16deb34c9e64
ms.openlocfilehash: da35f209b632bdf9e4ab2298239a505df69d6048
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59125730"
---
# <a name="xshared-attribute"></a>Atributo x:Shared
Quando definido como `false`, modifica o comportamento de recuperação de recursos do WPF para que as solicitações para o recurso atribuído criam uma nova instância para cada solicitação em vez de compartilhar a mesma instância para todas as solicitações.  
  
## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML  
  
```xaml  
<ResourceDictionary>  
  <object x:Shared="false".../>  
</ResourceDictionary>  
```  
  
## <a name="remarks"></a>Comentários  
 `x:Shared` é mapeado para o namespace XAML de linguagem XAML e é reconhecido como um elemento de linguagem XAML válido por serviços XAML do .NET Framework e seus leitores XAML. No entanto, os recursos indicados do `x:Shared` só são relevantes para aplicativos WPF e o analisador de XAML WPF. No WPF, `x:Shared` só é útil como um atributo quando ele é aplicado a um objeto que existe dentro de um WPF <xref:System.Windows.ResourceDictionary>. Outros usos não lançam exceções de análise ou outros erros, mas eles não têm nenhum efeito.  
  
 O significado de `x:Shared` não for especificado na especificação da linguagem XAML. Outras implementações de XAML, como aqueles que se baseiam em serviços de XAML do .NET Framework, não necessariamente oferecem suporte de compartilhamento de recursos. Essas implementações de XAML pode fornecer um comportamento semelhante na estrutura de suporte que também usada `x:Shared` valores.  
  
 No WPF, o padrão `x:Shared` condição para os recursos é `true`. Essa condição significa que qualquer solicitação de determinado recurso sempre retorna a mesma instância.  
  
 Modificando um objeto que é retornado por meio de um recurso de API, como <xref:System.Windows.FrameworkElement.FindResource%2A>, ou modificando um objeto diretamente em um <xref:System.Windows.ResourceDictionary>, modifica o recurso original. Se as referências a esse recurso foram referências a recursos dinâmicos, os consumidores do recurso obtém o recurso alterado.  
  
 Se as referências para o recurso de referências de recursos estáticos, altera o recurso após [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] tempo de processamento são irrelevantes. Para obter mais informações sobre estáticos em comparação com referências a recursos dinâmicos, consulte [recursos XAML](../wpf/advanced/xaml-resources.md).  
  
 Especificando explicitamente `x:Shared="true"` raramente é feito, pois esse já é o padrão. Não há nenhum código direto equivalente para `x:Shared` modelo de objeto no WPF; ele só pode ser especificado em um uso XAML e deve ser processado pelo comportamento padrão do WPF ou em um fluxo de nó XAML intermediário no caminho de carga se processados usando o .NET Framework XAML Se rvices e seus leitores XAML.  
  
 Um cenário para `x:Shared="false"` é se você definir um <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement> derivado da classe como um recurso e, em seguida, você introduzir o recurso de elemento em um modelo de conteúdo. `x:Shared="false"` permite que um recurso do elemento a ser introduzido várias vezes na mesma coleção (como um <xref:System.Windows.Controls.UIElementCollection>). Sem `x:Shared="false"` isso é inválido porque a coleção impõe a exclusividade de seu conteúdo. No entanto, o `x:Shared="false"` comportamento cria outra instância idêntica do recurso em vez de retornar a mesma instância.  
  
 Outro cenário para `x:Shared="false"` é se você usar um <xref:System.Windows.Freezable> recursos para valores de animação, mas deseja modificar o recurso em uma base da animação.  
  
 A manipulação de cadeia de caracteres de `false` não diferencia maiusculas de minúsculas.  
  
 No WPF, `x:Shared` só é válida nas seguintes condições:  
  
-   O <xref:System.Windows.ResourceDictionary> que contém os itens com `x:Shared` deve ser compilado. O <xref:System.Windows.ResourceDictionary> não pode estar dentro do XAML flexível ou usado para temas.  
  
-   O <xref:System.Windows.ResourceDictionary> que contém os itens não deve ser aninhado dentro de outra <xref:System.Windows.ResourceDictionary>. Por exemplo, você não pode usar `x:Shared` para itens em uma <xref:System.Windows.ResourceDictionary> que está em um <xref:System.Windows.Style> que já está um <xref:System.Windows.ResourceDictionary> item.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.ResourceDictionary>
- [Recursos XAML](../wpf/advanced/xaml-resources.md)
- [Elementos base](../wpf/advanced/base-elements.md)
