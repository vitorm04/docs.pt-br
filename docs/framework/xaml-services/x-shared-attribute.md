---
title: Atributo x:Shared
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], x:Shared attribute
- x:Shared attribute [XAML Services]
- Shared attribute in XAML [XAML Services]
ms.assetid: c8cff434-2785-405f-9f95-16deb34c9e64
ms.openlocfilehash: bee37735382249d2919ef870ca495e6096532352
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="xshared-attribute"></a>Atributo x:Shared
Quando definido como `false`, modifica o comportamento de recuperação de recursos do WPF para que as solicitações para o recurso atribuído criam uma nova instância para cada solicitação, em vez de compartilhar a mesma instância para todas as solicitações.  
  
## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML  
  
```xaml  
<ResourceDictionary>  
  <object x:Shared="false".../>  
</ResourceDictionary>  
```  
  
## <a name="remarks"></a>Comentários  
 `x:Shared` é mapeado para o namespace XAML de linguagem XAML e é reconhecido como um elemento de linguagem XAML válido por serviços XAML do .NET Framework e seus leitores XAML. No entanto, os recursos declarados de `x:Shared` só são relevantes para aplicativos do WPF e para o analisador de WPF XAML. No WPF, `x:Shared` só é útil como um atributo quando ele é aplicado a um objeto que existe dentro de um WPF <xref:System.Windows.ResourceDictionary>. Outros usos não emitem exceções de análise ou outros erros, mas eles não têm nenhum efeito.  
  
 O significado de `x:Shared` não for especificado na especificação de linguagem XAML. Outras implementações de XAML, como aqueles com base nos serviços de XAML do .NET Framework, não necessariamente oferecem suporte de compartilhamento de recursos. Tais implementações de XAML podem fornecer um comportamento semelhante na estrutura de suporte que também usado `x:Shared` valores.  
  
 No WPF, o padrão `x:Shared` condição de recursos é `true`. Esta condição significa que qualquer solicitação de determinado recurso sempre retorna a mesma instância.  
  
 Modificando um objeto que é retornado por meio de um recurso de API, como <xref:System.Windows.FrameworkElement.FindResource%2A>, ou modificando um objeto diretamente em um <xref:System.Windows.ResourceDictionary>, modifica o recurso original. Se as referências a esse recurso referências a recursos dinâmicos, os consumidores do recurso ter alterado do recurso.  
  
 Se a referência ao recurso fosse estática, mudanças no recurso após [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] tempo de processamento são irrelevantes. Para obter mais informações sobre estática em vez de referências a recursos dinâmicos, consulte [recursos XAML](../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
 Especificando explicitamente `x:Shared="true"` raramente é feita, pois já é o padrão. Não há nenhum código direto equivalente para `x:Shared` modelo de objeto no WPF; ele só pode ser especificado no uso de XAML e deve ser processado pelo comportamento padrão do WPF ou em um fluxo do nó XAML intermediário no caminho de carga se processado usando o .NET Framework XAML Se rvices e seus leitores XAML.  
  
 Um cenário para `x:Shared="false"` é se você definir um <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement> derivado da classe como um recurso e, em seguida, você introduzir o recurso de elemento em um modelo de conteúdo. `x:Shared="false"` permite que um recurso de elemento ser introduzido várias vezes na mesma coleção (como um <xref:System.Windows.Controls.UIElementCollection>). Sem `x:Shared="false"` isso é inválido porque a coleção impõe a exclusividade de seu conteúdo. No entanto, o `x:Shared="false"` comportamento cria outra instância idêntica do recurso em vez de retornar a mesma instância.  
  
 Outro cenário para `x:Shared="false"` é se você usar um <xref:System.Windows.Freezable> recursos para valores de animação, mas você deseja modificar o recurso em uma base por animação.  
  
 A manipulação de cadeia de caracteres de `false` não diferencia maiusculas de minúsculas.  
  
 No WPF, `x:Shared` só é válida nas seguintes condições:  
  
-   O <xref:System.Windows.ResourceDictionary> que contém os itens com `x:Shared` devem ser compiladas. O <xref:System.Windows.ResourceDictionary> não pode estar em XAML flexível ou usado para temas.  
  
-   O <xref:System.Windows.ResourceDictionary> que contém os itens não podem ser aninhados dentro de outra <xref:System.Windows.ResourceDictionary>. Por exemplo, você não pode usar `x:Shared` para itens em uma <xref:System.Windows.ResourceDictionary> que está dentro um <xref:System.Windows.Style> que já é um <xref:System.Windows.ResourceDictionary> item.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.ResourceDictionary>  
 [Recursos XAML](../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [Elementos base](../../../docs/framework/wpf/advanced/base-elements.md)
