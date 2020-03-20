---
title: Propriedades de dependência somente leitura
ms.date: 03/30/2017
helpviewer_keywords:
- dependency properties [WPF], read-only
- read-only dependency properties [WPF]
ms.assetid: f23d6ec9-3780-4c09-a2ff-b2f0a2deddf1
ms.openlocfilehash: 8adc90182f0f42f52e6ace4e13c68acb3539516b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187176"
---
# <a name="read-only-dependency-properties"></a>Propriedades de dependência somente leitura
Este tópico descreve propriedades de dependência somente leitura, incluindo as propriedades de dependência somente leitura existentes e os cenários e técnicas para criação de uma propriedade de dependência somente leitura personalizada.  

<a name="prerequisites"></a>
## <a name="prerequisites"></a>Pré-requisitos  
 Este tópico pressupõe que você compreenda os cenários básicos de implementar uma propriedade de dependência e como os metadados são aplicados a uma propriedade de dependência personalizada. Consulte [Propriedades de dependência personalizadas](custom-dependency-properties.md) e [Metadados de propriedade de dependência](dependency-property-metadata.md) para ver o contexto.  
  
<a name="existing"></a>
## <a name="existing-read-only-dependency-properties"></a>Propriedades de dependência somente leitura existentes  
 Algumas das propriedades de dependência definidas na estrutura de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] são somente leitura. A razão típica para especificar uma propriedade de dependência somente leitura é que elas são propriedades que devem ser usadas para determinação do estado, mas quando esse estado é influenciado por uma variedade de fatores. No entanto, apenas configurar a propriedade para esse estado não é desejável de uma perspectiva de design de interface do usuário. Por exemplo, <xref:System.Windows.UIElement.IsMouseOver%2A> a propriedade é realmente apenas um estado de superfície, conforme determinado a partir da entrada do mouse. Qualquer tentativa de definir esse valor de maneira programática evitando a entrada de mouse verdadeira seria imprevisível e poderia causar inconsistência.  
  
 Em virtude de não ser configurável, propriedades de dependência somente leitura não são adequadas para muitos dos cenários para os quais as propriedades de dependência normalmente oferecem uma solução (por exemplo, vinculação de dados, estilizável diretamente para um valor, validação, animação, herança). Apesar de não serem configuráveis, as propriedades de dependência somente leitura ainda têm alguns recursos adicionais com suporte de propriedades de dependência no sistema de propriedades. A capacidade restante mais importante é que a propriedade de dependência somente leitura ainda pode ser usada como um gatilho de propriedade em um estilo. Você não pode habilitar gatilhos com uma propriedade normal de tempo de execução de linguagem comum (CLR); ele precisa ser uma propriedade de dependência. A propriedade acima <xref:System.Windows.UIElement.IsMouseOver%2A> mencionada é um exemplo perfeito de um cenário onde pode ser bastante útil definir um estilo para um controle, onde alguma propriedade visível, como um fundo, primeiro plano ou propriedades similares de elementos compostos dentro do controle mudará quando o usuário coloca um mouse sobre alguma região definida do seu controle. Alterações em uma propriedade de dependência somente leitura também podem ser detectadas e relatadas pelos processos de invalidação inerentes do sistema de propriedades e isso na verdade dá suporte à funcionalidade de gatilho de propriedade internamente.  
  
<a name="new"></a>
## <a name="creating-custom-read-only-dependency-properties"></a>Criando propriedades de dependência somente leitura personalizadas  
 Certifique-se de ler a seção acima sobre por que as propriedades de dependência somente leitura não funcionarão para muitos cenários típicos de propriedade de dependência. Mas, se tiver um cenário apropriado, você poderá querer criar sua própria propriedade de dependência somente leitura.  
  
 Grande parte do processo de criar uma propriedade de dependência somente leitura é igual ao processo descrito nos tópicos [Propriedades de dependência personalizadas](custom-dependency-properties.md) e [Implementar uma propriedade de dependência](how-to-implement-a-dependency-property.md). Há três diferenças importantes:  
  
- Ao registrar sua propriedade, <xref:System.Windows.DependencyProperty.RegisterReadOnly%2A> ligue para <xref:System.Windows.DependencyProperty.Register%2A> o método em vez do método normal para registro de propriedades.  
  
- Ao implementar a propriedade "wrapper" CLR, certifique-se de que o invólucro também não tenha uma implementação definida, para que não haja inconsistência no estado somente leitura para o invólucro público que você expõe.  
  
- O objeto devolvido pelo registro somente <xref:System.Windows.DependencyPropertyKey> leitura <xref:System.Windows.DependencyProperty>é em vez de . Você ainda deve armazenar esse campo como um membro, mas normalmente você não faria dele um membro público do tipo.  
  
 Qualquer valor ou campo particular que você tiver como suporte para sua propriedade de dependência somente leitura pode ser totalmente gravável usando qualquer lógica que você decidir. No entanto, a maneira mais simples de definir a propriedade inicialmente ou como parte da lógica de tempo de execução é usar as APIs do sistema de propriedade, em vez de contornar o sistema de propriedade e definir o campo de apoio privado diretamente. Em particular, há uma <xref:System.Windows.DependencyObject.SetValue%2A> assinatura que aceita um <xref:System.Windows.DependencyPropertyKey>parâmetro do tipo . Como e onde você define esse valor de forma programática dentro da <xref:System.Windows.DependencyPropertyKey> lógica do aplicativo afetará a forma como você pode desejar definir o acesso no criado quando você registrou a propriedade de dependência pela primeira vez. Se manipular toda essa lógica dentro da classe, você pode torná-la particular ou, se exigir que ela seja definida de outras partes do assembly, poderá defini-la como interna. Uma abordagem <xref:System.Windows.DependencyObject.SetValue%2A> é chamar dentro de um manipulador de eventos de classe de um evento relevante que informa uma instância de classe que o valor da propriedade armazenada precisa ser alterado. Outra abordagem é amarrar as propriedades <xref:System.Windows.PropertyChangedCallback> de <xref:System.Windows.CoerceValueCallback> dependência em conjunto usando os retornos emparelhados e de chamada como parte dos metadados dessas propriedades durante o registro.  
  
 Como <xref:System.Windows.DependencyPropertyKey> o é privado e não é propagado pelo sistema de propriedade fora do seu código, uma propriedade de dependência somente leitura tem segurança de configuração melhor do que uma propriedade de dependência de leitura e gravação. Para uma propriedade de dependência de leitura/gravação, o campo de identificação é implicitamente ou explicitamente público e, portanto, a propriedade é amplamente configurável. Para obter informações mais específicas, consulte [Segurança das propriedades de dependência](dependency-property-security.md).  
  
## <a name="see-also"></a>Confira também

- [Visão geral das propriedades de dependência](dependency-properties-overview.md)
- [Propriedades de dependência personalizada](custom-dependency-properties.md)
- [Estilo e modelagem](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
