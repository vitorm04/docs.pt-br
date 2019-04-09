---
title: Padrões de evento fraco
ms.date: 03/30/2017
helpviewer_keywords:
- weak event pattern implementation [WPF]
- event handlers [WPF], weak event pattern
- IWeakEventListener interface [WPF]
ms.assetid: e7c62920-4812-4811-94d8-050a65c856f6
ms.openlocfilehash: 49795235d489ebc70cec11332e6be4a9452bc21d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59139250"
---
# <a name="weak-event-patterns"></a>Padrões de evento fraco
Em aplicativos, é possível que manipuladores que estão anexados a origens de eventos não sejam destruídos em coordenação com o objeto de ouvinte que anexou o manipulador à origem. Essa situação pode levar a vazamentos de memória. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] apresenta um padrão de design que pode ser usado para resolver esse problema, fornecendo uma classe de gerenciamento dedicada para determinados eventos e implementando uma interface em ouvintes para o evento. Esse padrão de design é conhecido como o *padrão de evento fraco*.  
  
## <a name="why-implement-the-weak-event-pattern"></a>Por que implementar o padrão de evento fraco?  
 Escutar eventos pode levar a vazamentos de memória. A técnica comum para ouvir um evento é usar a sintaxe específica a um idioma que anexa um manipulador a um evento em uma fonte. Por exemplo, em C#, que a sintaxe é: `source.SomeEvent += new SomeEventHandler(MyEventHandler)`.  
  
 Essa técnica cria uma referência forte da origem do evento para o ouvinte de eventos. Normalmente, anexar um manipulador de eventos para um ouvinte faz com que o ouvinte tenha um tempo de vida do objeto que é influenciado pelo tempo de vida do objeto da origem (a menos que o manipulador de eventos seja explicitamente removido). Mas, em determinadas circunstâncias, você pode desejar que o tempo de vida do objeto do ouvinte seja controlado por outros fatores, como se ele pertencesse à árvore visual do aplicativo e não pelo tempo de vida de origem. Sempre que o tempo de vida do objeto de origem ultrapassa o tempo de vida do objeto do ouvinte, o padrão de eventos normal ocasiona um vazamento de memória: o ouvinte é mantido ativo mais que o previsto.  
  
 O padrão de evento fraco é projetado para resolver esse problema de vazamento de memória. O padrão de evento fraco pode ser usado sempre que um ouvinte precisa registrar um evento, mas não sabe explicitamente quando cancelar o registro. O padrão de evento fraco também pode ser usado sempre que o tempo de vida do objeto de origem exceder o tempo de vida útil do objeto do ouvinte. (Nesse caso, o que é *útil* é determinado por você.) O padrão de evento fraco permite que o ouvinte registre e receba o evento sem afetar as características de tempo de vida do objeto do ouvinte. Na verdade, a referência implícita da origem não determina se o ouvinte está qualificado para coleta de lixo. A referência é uma referência fraca, por isso a nomenclatura de padrão de evento fraco e [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] relacionado. O ouvinte pode ter o lixo coletado ou destruído, e a origem pode continuar sem reter manipulador referências não colecionáveis do manipulador para um objeto agora destruído.  
  
## <a name="who-should-implement-the-weak-event-pattern"></a>Por que implementar o padrão de evento fraco?  
 Implementar o padrão de evento fraco é interessante principalmente para autores de controle. Como um autor de controle, você é basicamente responsável pelo comportamento e confinamento de seu controle e o impacto em aplicativos em que ele é inserido. Isso inclui o comportamento de tempo de vida do objeto de controle, em particular, o tratamento do problema de vazamento de memória descrito.  
  
 Determinados cenários prestam-se inerentemente ao aplicativo do padrão de evento fraco. Um cenário é a associação de dados. Na associação de dados, é comum que o objeto de origem seja completamente independente do objeto de ouvinte, que é um destino de uma associação. Muitos aspectos da associação de dados [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] já têm o padrão de evento fraco aplicado em como os eventos são implementados.  
  
## <a name="how-to-implement-the-weak-event-pattern"></a>Como implementar o padrão de evento fraco  
 Há três maneiras de implementar o padrão de evento fraco. A tabela a seguir lista as três abordagens e fornece algumas diretrizes sobre quando usar cada uma.  
  
|Abordagem|Quando implementar|  
|--------------|-----------------------|  
|Usar uma classe existente de gerenciamento de evento fraco|Se o evento que você deseja assinar tiver um correspondente <xref:System.Windows.WeakEventManager>, use o Gerenciador de evento fraco existente. Para obter uma lista de gerenciadores de evento fraco incluídos com o WPF, consulte a hierarquia de herança na <xref:System.Windows.WeakEventManager> classe. Como os gerenciadores de evento fraco incluídos são limitados, provavelmente você precisará escolher uma das outras abordagens.|  
|Usar uma classe de gerenciador de evento fraco genérico|Usar um genérico <xref:System.Windows.WeakEventManager%602> quando um existente <xref:System.Windows.WeakEventManager> está indisponível, você deseja uma maneira fácil de implementar, e você não estiver preocupado com eficiência. Genérica <xref:System.Windows.WeakEventManager%602> é menos eficiente do que um Gerenciador de evento fraco existente ou personalizado. Por exemplo, a classe genérica faz mais reflexão para descobrir o evento que recebeu o nome do evento. Além disso, o código para registrar o evento usando o genérico <xref:System.Windows.WeakEventManager%602> é mais detalhado do que usar um existente ou personalizado <xref:System.Windows.WeakEventManager>.|  
|Criar uma classe de gerenciador de evento fraco personalizado|Criar um personalizado <xref:System.Windows.WeakEventManager> quando um existente <xref:System.Windows.WeakEventManager> não está disponível e você deseja a melhor eficiência. Usando um personalizado <xref:System.Windows.WeakEventManager> para assinar um evento será mais eficiente, mas você aumentará o custo de escrever um código no início.|  
|Usar um Gerenciador de evento fraco de terceiros|O NuGet tem [vários gerenciadores de evento fraco](https://www.nuget.org/packages?q=weak+event+manager&prerel=false) e várias estruturas WPF também suportam o padrão (por exemplo, consulte [documentação do Prism na assinatura de evento livremente acoplado](https://github.com/PrismLibrary/Prism-Documentation/blob/master/docs/wpf/Communication.md#subscribing-to-events)).|

 As seções a seguir descrevem como implementar o padrão de evento fraco.  Para fins desta discussão, o evento que deve ser assinado tem as seguintes características.  
  
-   O nome do evento é `SomeEvent`.  
  
-   O evento é gerado pela classe `EventSource`.  
  
-   O manipulador de eventos tem o tipo: `SomeEventEventHandler` (ou `EventHandler<SomeEventEventArgs>`).  
  
-   O evento passa um parâmetro do tipo `SomeEventEventArgs` aos manipuladores de eventos.  
  
### <a name="using-an-existing-weak-event-manager-class"></a>Usar uma classe existente de gerenciador de evento fraco  
  
1.  Encontre um gerenciador de evento fraco existente.  
  
     Para obter uma lista de gerenciadores de evento fraco incluídos com o WPF, consulte a hierarquia de herança na <xref:System.Windows.WeakEventManager> classe.  
  
2.  Use o novo gerenciador de evento fraco em vez da conexão de evento normal.  
  
     Por exemplo, se seu código usa o padrão a seguir para assinar um evento:  
  
    ```  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     Altere-o para o seguinte padrão:  
  
    ```  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     Da mesma forma, se seu código usa o padrão a seguir para cancelar a assinatura de um evento:  
  
    ```  
    source.SomeEvent -= new SomeEventEventHandler(OnSome);  
    ```  
  
     Altere-o para o seguinte padrão:  
  
    ```  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
### <a name="using-the-generic-weak-event-manager-class"></a>Usando uma classe de gerenciador de evento fraco genérico  
  
1.  Usar o genérico <xref:System.Windows.WeakEventManager%602> classe em vez da conexão de evento normal.  
  
     Quando você usa <xref:System.Windows.WeakEventManager%602> para registrar ouvintes de eventos, você fornece a origem do evento e <xref:System.EventArgs> tipo de como os parâmetros de tipo para a classe e a chamada <xref:System.Windows.WeakEventManager%602.AddHandler%2A> conforme mostrado no código a seguir:  
  
    ```  
    WeakEventManager<EventSource, SomeEventEventArgs>.AddHandler(source, "SomeEvent", source_SomeEvent);  
    ```  
  
### <a name="creating-a-custom-weak-event-manager-class"></a>Criando uma classe de gerenciador de evento fraco personalizado  
  
1.  Copie o seguinte modelo de classe no seu projeto.  
  
     Essa classe herda a <xref:System.Windows.WeakEventManager> classe.  
  
     [!code-csharp[WeakEvents#WeakEventManagerTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/WeakEvents/CSharp/WeakEventManagerTemplate.cs#weakeventmanagertemplate)]  
  
2.  Substitua o nome `SomeEventWeakEventManager` pelo seu próprio nome.  
  
3.  Substitua os três nomes descritos anteriormente pelos nomes correspondentes para seu evento. (`SomeEvent`, `EventSource` e `SomeEventEventArgs`)  
  
4.  Defina a visibilidade (pública/interna/privada) da classe de gerenciador de evento fraco para a mesma visibilidade que o evento que ele gerencia.  
  
5.  Use o novo gerenciador de evento fraco em vez da conexão de evento normal.  
  
     Por exemplo, se seu código usa o padrão a seguir para assinar um evento:  
  
    ```  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     Altere-o para o seguinte padrão:  
  
    ```  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     De modo semelhante, se seu código usa o padrão a seguir para assinar um evento:  
  
    ```  
    source.SomeEvent -= new SomeEventEventHandler(OnSome);  
    ```  
  
     Altere-o para o seguinte padrão:  
  
    ```  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.WeakEventManager>
- <xref:System.Windows.IWeakEventListener>
- [Visão geral de eventos roteados](routed-events-overview.md)
- [Visão geral da vinculação de dados](../data/data-binding-overview.md)
