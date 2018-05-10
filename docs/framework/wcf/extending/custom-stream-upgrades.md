---
title: Atualizações de fluxo personalizadas
ms.date: 03/30/2017
ms.assetid: e3da85c8-57f3-4e32-a4cb-50123f30fea6
ms.openlocfilehash: 84edac7a4dbaaf1a01332f5c0af29319c279dd1b
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
---
# <a name="custom-stream-upgrades"></a>Atualizações de fluxo personalizadas
Transportes orientado por fluxo, como TCP e Pipes nomeados operam em um fluxo contínuo de bytes entre o cliente e servidor. Esse fluxo é realizado por um <xref:System.IO.Stream> objeto. Em uma atualização de fluxo, o cliente deseja adicionar uma camada de protocolo opcional para a pilha de canais e solicita que a outra extremidade do canal de comunicação para fazer isso. A atualização de fluxo consiste na substituição original <xref:System.IO.Stream> objeto com um atualizado.  
  
 Por exemplo, você pode criar um fluxo de compactação diretamente sobre o fluxo de transporte. Nesse caso, o transporte original <xref:System.IO.Stream> é substituído por um que encapsula a compressão <xref:System.IO.Stream> em torno do original.  
  
 Você pode aplicar várias atualizações de fluxo, cada encapsulamento anterior.  
  
## <a name="how-stream-upgrades-work"></a>Como as atualizações de fluxo de trabalho  
 Existem quatro componentes para o processo de atualização de fluxo.  
  
1.  Um fluxo de atualização *iniciador* inicia o processo: em tempo de execução, ele pode iniciar uma solicitação para a outra extremidade da sua conexão para atualizar a camada de transporte de canal.  
  
2.  Um fluxo de atualização *Aceitante* executa a atualização: em tempo de execução ele recebe a solicitação de atualização de outro computador e, se possível, aceita a atualização.  
  
3.  Uma atualização *provedor* cria o *iniciador* no cliente e o *Aceitante* no servidor.  
  
4.  Uma atualização de fluxo *elemento de associação* é adicionada para as associações de serviço e o cliente e cria o provedor em tempo de execução.  
  
 Observe que no caso de várias atualizações, o iniciador e Aceitante encapsulam máquinas de estado para impor as transições de atualização são válidas para cada inicialização.  
  
## <a name="how-to-implement-a-stream-upgrade"></a>Como implementar uma atualização de fluxo  
 Windows Communication Foundation (WCF) fornece quatro `abstract` classes que você pode implementar:  
  
-   <xref:System.ServiceModel.Channels.StreamUpgradeInitiator?displayProperty=nameWithType>  
  
-   <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor?displayProperty=nameWithType>  
  
-   <xref:System.ServiceModel.Channels.StreamUpgradeProvider?displayProperty=nameWithType>  
  
-   <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement?displayProperty=nameWithType>  
  
 Para implementar uma atualização de fluxo personalizados, faça o seguinte: Esse procedimento implementa um processo de atualização de fluxo mínimo nos computadores cliente e servidor.  
  
1.  Criar uma classe que implementa <xref:System.ServiceModel.Channels.StreamUpgradeInitiator>.  
  
    1.  Substituir o <xref:System.ServiceModel.Channels.StreamUpgradeInitiator.InitiateUpgrade%2A> método entrem no fluxo a ser atualizado e retornar o fluxo atualizado. Esse método funciona de forma síncrona; Há métodos análogos ao iniciar a atualização de forma assíncrona.  
  
    2.  Substituir o <xref:System.ServiceModel.Channels.StreamUpgradeInitiator.GetNextUpgrade%2A> método para verificar se há atualizações adicionais.  
  
2.  Criar uma classe que implementa <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor>.  
  
    1.  Substituir o <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor.AcceptUpgrade%2A> método entrem no fluxo a ser atualizado e retornar o fluxo atualizado. Esse método funciona de forma síncrona; Há métodos análogos a aceitar a atualização de forma assíncrona.  
  
    2.  Substituir o <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor.CanUpgrade%2A> método para determinar se a atualização solicitada é suportada por esta atualização aceitante neste momento no processo de atualização.  
  
3.  Criar uma classe de implementa <xref:System.ServiceModel.Channels.StreamUpgradeProvider>. Substituir o <xref:System.ServiceModel.Channels.StreamUpgradeProvider.CreateUpgradeAcceptor%2A> e <xref:System.ServiceModel.Channels.StreamUpgradeProvider.CreateUpgradeInitiator%2A> métodos para retornar instâncias do aceitante e iniciador definidas nas etapas 2 e 1.  
  
4.  Criar uma classe que implementa <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement>.  
  
    1.  Substituir o <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement.BuildClientStreamUpgradeProvider%2A> método no cliente e o <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement.BuildServerStreamUpgradeProvider%2A> método no serviço.  
  
    2.  Substituir o <xref:System.ServiceModel.Channels.BindingElement.BuildChannelFactory%2A> método no cliente e o <xref:System.ServiceModel.Channels.BindingElement.BuildChannelListener%2A> método no serviço para adicionar o elemento de associação de atualização para <xref:System.ServiceModel.Channels.BindingContext.BindingParameters%2A>.  
  
5.  Adicione o novo elemento de associação de atualização de fluxo para associações nos computadores cliente e servidor.  
  
## <a name="security-upgrades"></a>Atualizações de segurança  
 Adicionar uma atualização de segurança é uma versão especializada do processo de atualização de fluxo geral.  
  
 WCF já fornece dois elementos de associação para a atualização de segurança de fluxo. A configuração de segurança em nível de transporte é encapsulada pelo <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement> e <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement> que pode ser configurado e adicionado a uma associação personalizada. Esses elementos de associação estendem o <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement> classe que cria o fluxo de cliente e servidor de atualização de provedores. Esses elementos de associação tem métodos que criam o fluxo de segurança especializados classes de provedor de atualização, que não são `public`, portanto, para esses dois casos tudo o que você precisa fazer é adicionar o elemento de associação para a associação.  
  
 Para cenários de segurança não é atendidos com os elementos de associação de dois acima, três relacionadas à segurança `abstract` classes derivam as classes base iniciador, aceitante e provedor acima:  
  
1.  <xref:System.ServiceModel.Channels.StreamSecurityUpgradeInitiator?displayProperty=nameWithType>  
  
2.  <xref:System.ServiceModel.Channels.StreamSecurityUpgradeAcceptor?displayProperty=nameWithType>  
  
3.  <xref:System.ServiceModel.Channels.StreamSecurityUpgradeProvider?displayProperty=nameWithType>  
  
 O processo de implementação de uma atualização de fluxo de segurança é o mesmo de antes, com a diferença de que você deve derivar desses três classes. Substitua as propriedades adicionais nessas classes para fornecer informações de segurança para o tempo de execução.  
  
## <a name="multiple-upgrades"></a>Várias atualizações  
 Para criar outras solicitações de atualização Repita o processo acima: criar extensões adicionais de <xref:System.ServiceModel.Channels.StreamUpgradeProvider> e elementos de associação. Adicione os elementos de associação para a associação. Os elementos de associação adicionais são processados em sequência, começando com o primeiro elemento de associação adicionado para a associação. Em <xref:System.ServiceModel.Channels.BindingElement.BuildChannelFactory%2A> e <xref:System.ServiceModel.Channels.BindingElement.BuildChannelListener%2A> cada provedor de atualização pode determinar como camada próprio em qualquer atualização pré-existentes parâmetros de associação. Em seguida, ele deve substituir a associação de parâmetro com um novo parâmetro de associação de atualização composto de atualização existente.  
  
 Como alternativa, um provedor de atualização pode dar suporte a várias atualizações. Por exemplo, você talvez queira implementar um provedor de atualização de fluxo personalizados que oferece suporte à segurança e compactação. Siga as etapas a seguir:  
  
1.  Subclasse <xref:System.ServiceModel.Channels.StreamSecurityUpgradeProvider> para gravar a classe de provedor que cria o iniciador e Aceitante.  
  
2.  Subclasse o <xref:System.ServiceModel.Channels.StreamSecurityUpgradeInitiator> certificando-se de substituir o <xref:System.ServiceModel.Channels.StreamUpgradeInitiator.GetNextUpgrade%2A> método para retornar os tipos de conteúdo para o fluxo de compactação e o seguro em ordem.  
  
3.  Subclasse o <xref:System.ServiceModel.Channels.StreamSecurityUpgradeAcceptor> que compreende os tipos de conteúdo personalizados em seu <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor.CanUpgrade%2A> método.  
  
4.  O fluxo será atualizado após cada chamada para <xref:System.ServiceModel.Channels.StreamUpgradeInitiator.GetNextUpgrade%2A> e <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor.CanUpgrade%2A>.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Channels.StreamUpgradeInitiator>  
 <xref:System.ServiceModel.Channels.StreamSecurityUpgradeInitiator>  
 <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor>  
 <xref:System.ServiceModel.Channels.StreamSecurityUpgradeAcceptor>  
 <xref:System.ServiceModel.Channels.StreamUpgradeProvider>  
 <xref:System.ServiceModel.Channels.StreamSecurityUpgradeProvider>  
 <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement>  
 <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
 <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>
