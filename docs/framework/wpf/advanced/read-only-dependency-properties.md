---
title: Propriedades de dependência somente leitura
ms.date: 03/30/2017
helpviewer_keywords:
- dependency properties [WPF], read-only
- read-only dependency properties [WPF]
ms.assetid: f23d6ec9-3780-4c09-a2ff-b2f0a2deddf1
ms.openlocfilehash: 2850dd86ffbe2c6698821218dee5d870fc58e89b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="read-only-dependency-properties"></a>Propriedades de dependência somente leitura
Este tópico descreve propriedades de dependência somente leitura, incluindo as propriedades de dependência somente leitura existentes e os cenários e técnicas para criação de uma propriedade de dependência somente leitura personalizada.  
  

  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Pré-requisitos  
 Este tópico pressupõe que você compreenda os cenários básicos de implementar uma propriedade de dependência e como os metadados são aplicados a uma propriedade de dependência personalizada. Consulte [Propriedades de dependência personalizadas](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md) e [Metadados de propriedade de dependência](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md) para ver o contexto.  
  
<a name="existing"></a>   
## <a name="existing-read-only-dependency-properties"></a>Propriedades de dependência somente leitura existentes  
 Algumas das propriedades de dependência definidas na estrutura de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] são somente leitura. A razão típica para especificar uma propriedade de dependência somente leitura é que elas são propriedades que devem ser usadas para determinação do estado, mas quando esse estado é influenciado por uma variedade de fatores. No entanto, apenas configurar a propriedade para esse estado não é desejável de uma perspectiva de design de interface do usuário. Por exemplo, a propriedade <xref:System.Windows.UIElement.IsMouseOver%2A> apenas adicionar estado conforme determinado do mouse de entrada. Qualquer tentativa de definir esse valor de maneira programática evitando a entrada de mouse verdadeira seria imprevisível e poderia causar inconsistência.  
  
 Em virtude de não ser configurável, propriedades de dependência somente leitura não são adequadas para muitos dos cenários para os quais as propriedades de dependência normalmente oferecem uma solução (por exemplo, vinculação de dados, estilizável diretamente para um valor, validação, animação, herança). Apesar de não serem configuráveis, as propriedades de dependência somente leitura ainda têm alguns recursos adicionais com suporte de propriedades de dependência no sistema de propriedades. A capacidade restante mais importante é que a propriedade de dependência somente leitura ainda pode ser usada como um gatilho de propriedade em um estilo. Não é possível habilitar gatilhos com uma propriedade [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] normal; ela precisa ser uma propriedade de dependência. O mencionados acima <xref:System.Windows.UIElement.IsMouseOver%2A> propriedade é um exemplo perfeito de um cenário em que pode ser muito útil definir um estilo para um controle, onde algumas propriedade visível como um plano de fundo, primeiro plano ou propriedades semelhantes de elementos compostos dentro de controle será alterado quando o usuário coloca o mouse sobre alguns definido região do seu controle. Alterações em uma propriedade de dependência somente leitura também podem ser detectadas e relatadas pelos processos de invalidação inerentes do sistema de propriedades e isso na verdade dá suporte à funcionalidade de gatilho de propriedade internamente.  
  
<a name="new"></a>   
## <a name="creating-custom-read-only-dependency-properties"></a>Criando propriedades de dependência somente leitura personalizadas  
 Certifique-se de ler a seção acima sobre por que as propriedades de dependência somente leitura não funcionarão para muitos cenários típicos de propriedade de dependência. Mas, se tiver um cenário apropriado, você poderá querer criar sua própria propriedade de dependência somente leitura.  
  
 Grande parte do processo de criar uma propriedade de dependência somente leitura é igual ao processo descrito nos tópicos [Propriedades de dependência personalizadas](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md) e [Implementar uma propriedade de dependência](../../../../docs/framework/wpf/advanced/how-to-implement-a-dependency-property.md). Há três diferenças importantes:  
  
-   Ao registrar sua propriedade, chame o <xref:System.Windows.DependencyProperty.RegisterReadOnly%2A> método em vez de normal <xref:System.Windows.DependencyProperty.Register%2A> método para o registro de propriedade.  
  
-   Ao implementar a propriedade "wrapper" [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)], certifique-se de que o wrapper também não tenha uma implementação definida, para que não haja nenhuma inconsistência no estado somente leitura para o wrapper público que será exposto.  
  
-   O objeto retornado pelo registro somente leitura é <xref:System.Windows.DependencyPropertyKey> em vez de <xref:System.Windows.DependencyProperty>. Você ainda deve armazenar esse campo como um membro, mas normalmente você não faria dele um membro público do tipo.  
  
 Qualquer valor ou campo particular que você tiver como suporte para sua propriedade de dependência somente leitura pode ser totalmente gravável usando qualquer lógica que você decidir. No entanto, a maneira mais simples de configurar a propriedade inicialmente ou como parte da lógica de tempo de execução é usar o [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] do sistema de propriedades em vez de contornar o sistema de propriedades e configurar o campo de suporte privado diretamente. Em particular, há uma assinatura de <xref:System.Windows.DependencyObject.SetValue%2A> que aceita um parâmetro de tipo <xref:System.Windows.DependencyPropertyKey>. Como e onde você definir esse valor por meio de programação dentro de sua lógica de aplicativo afetará como talvez você queira definir o acesso a <xref:System.Windows.DependencyPropertyKey> criada quando você registrou primeiro a propriedade de dependência. Se manipular toda essa lógica dentro da classe, você pode torná-la particular ou, se exigir que ela seja definida de outras partes do assembly, poderá defini-la como interna. Uma abordagem é chamada <xref:System.Windows.DependencyObject.SetValue%2A> dentro de um manipulador de eventos de classe de um evento relevante que informa uma instância da classe que o valor da propriedade armazenado precisa ser alterado. Outra abordagem é reunir propriedades de dependência usando emparelhado <xref:System.Windows.PropertyChangedCallback> e <xref:System.Windows.CoerceValueCallback> retornos de chamada como parte dos metadados dessas propriedades durante o registro.  
  
 Porque o <xref:System.Windows.DependencyPropertyKey> é privado e não é propagada pelo sistema de propriedades fora de seu código, uma propriedade de dependência somente leitura ter a melhor configuração de segurança que uma propriedade de dependência de leitura / gravação. Para uma propriedade de dependência de leitura/gravação, o campo de identificação é implicitamente ou explicitamente público e, portanto, a propriedade é amplamente configurável. Para obter informações mais específicas, consulte [Segurança das propriedades de dependência](../../../../docs/framework/wpf/advanced/dependency-property-security.md).  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral das propriedades da dependência](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [Propriedades de dependência personalizada](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [Estilo e modelagem](../../../../docs/framework/wpf/controls/styling-and-templating.md)
