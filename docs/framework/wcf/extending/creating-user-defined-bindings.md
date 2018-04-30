---
title: Criando associações definidas pelo usuário
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- user-defined bindings [WCF]
ms.assetid: c4960675-d701-4bc9-b400-36a752fdd08b
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 05476adccca0deb5fd82b62f99f06939664cc876
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2018
---
# <a name="creating-user-defined-bindings"></a>Criando associações definidas pelo usuário
Há várias maneiras de criar associações não fornecidas pelo sistema:  
  
-   Criar uma associação personalizada, com base no <xref:System.ServiceModel.Channels.CustomBinding> classe, que é um contêiner que você preenche com elementos de associação. A associação personalizada é adicionada a um ponto de extremidade de serviço. Você pode criar a associação personalizada que o arquivo por meio de programação ou em uma configuração de aplicativo. Para usar um elemento de associação de um arquivo de configuração do aplicativo, o elemento de associação deve estender <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>. Para obter mais informações sobre associações personalizadas, consulte [associações personalizadas](../../../../docs/framework/wcf/extending/custom-bindings.md) e <xref:System.ServiceModel.Channels.CustomBinding>.  
  
-   Você pode criar uma classe que deriva de uma associação padrão. Por exemplo, você pode derivar uma classe de <xref:System.ServiceModel.WSHttpBinding> e substituir <xref:System.ServiceModel.Channels.CustomBinding.CreateBindingElements%2A> método para obter os elementos de associação e inserir um elemento de associação personalizada ou estabelecer um valor específico para segurança.  
  
-   Você pode criar um novo <xref:System.ServiceModel.Channels.Binding> tipo controlar completamente a implementação de associação inteira.  
  
## <a name="the-order-of-binding-elements"></a>A ordem dos elementos de associação  
 Cada elemento de associação representa uma etapa de processamento ao enviar ou receber mensagens. Em tempo de execução, elementos de associação criam os canais e ouvintes necessários para construir as pilhas de canal de entrada e saída.  
  
 Há três tipos principais de elementos de associação: elementos de associação de protocolo, codificação de elementos de associação e os elementos de associação de transporte.  
  
 Elementos de associação de protocolo – estes elementos representam etapas de processamento de nível superior que atuam em mensagens. Canais e ouvintes criados por esses elementos de associação podem adicionar, remover ou modificar o conteúdo da mensagem. Uma associação de determinado pode ter um número arbitrário de elementos de associação de protocolo, cada herdando <xref:System.ServiceModel.Channels.BindingElement>. [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] inclui vários elementos de associação de protocolo, incluindo o <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> e <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.  
  
 Codificação de elemento de ligação – essas representam elementos transformações entre uma mensagem e uma codificação pronto para transmissão na conexão. Típico [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] associações incluir exatamente um elemento de associação de codificação. Exemplos de codificação de elementos de associação a <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>, o <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>e o <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>. Se um elemento de associação de codificação não for especificado para uma associação, a codificação padrão será usada. O padrão é texto quando o transporte é HTTP e binários, caso contrário.  
  
 Elemento de associação de transporte esses elementos representam a transmissão de uma mensagem de codificação em um protocolo de transporte. Típico [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] associações incluir exatamente um elemento de associação de transporte, que herda de <xref:System.ServiceModel.Channels.TransportBindingElement>. Exemplos de elementos de associação de transporte de <xref:System.ServiceModel.Channels.TcpTransportBindingElement>, o <xref:System.ServiceModel.Channels.HttpTransportBindingElement>e o <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>.  
  
 Ao criar novas associações, a ordem dos elementos de associação adicionado é importante. Sempre adicione elementos de associação na seguinte ordem:  
  
|Camada|Opções|Necessária|  
|-----------|-------------|--------------|  
|Fluxo de transações|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement?displayProperty=nameWithType>|Não|  
|Confiabilidade|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement?displayProperty=nameWithType>|Não|  
|Segurança|<xref:System.ServiceModel.Channels.SecurityBindingElement?displayProperty=nameWithType>|Não|  
|Duplex composto|<xref:System.ServiceModel.Channels.CompositeDuplexBindingElement?displayProperty=nameWithType>|Não|  
|Codificando|Texto, binária, MTOM, personalizado|Sim*|  
|Transporte|TCP, denominado Pipes, HTTP, HTTPS, MSMQ, personalizado|Sim|  
  
 * Porque uma codificação é necessária para cada associação, se não for especificada uma codificação, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] adiciona uma codificação padrão para você. O padrão é texto/XML para os transportes HTTP e HTTPS e binários caso contrário.  
  
## <a name="creating-a-new-binding-element"></a>Criar um novo elemento de associação  
 Além de tipos derivados de <xref:System.ServiceModel.Channels.BindingElement> que são fornecidos pelo [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], você pode criar seus próprios elementos de associação. Isso lhe permite personalizar a maneira como a pilha de associações é criada e os componentes que entrar criando seu próprio <xref:System.ServiceModel.Channels.BindingElement> que pode ser composto com os outros tipos fornecidos pelo sistema na pilha.  
  
 Por exemplo, se você implementar um `LoggingBindingElement` que fornece a capacidade de registrar a mensagem para um banco de dados, você deve colocá-lo acima de um canal de transporte na pilha de canais. Nesse caso, o aplicativo cria uma associação personalizada que é composto de `LoggingBindingElement` com `TcpTransportBindingElement`, conforme mostrado no exemplo a seguir.  
  
```csharp  
Binding customBinding = new CustomBinding(  
  new LoggingBindingElement(),   
  new TcpTransportBindingElement()  
);  
```  
  
 Como você escreve seu novo elemento de associação depende de sua funcionalidade exata. Um dos exemplos de [transporte: UDP](../../../../docs/framework/wcf/samples/transport-udp.md), fornece uma descrição detalhada de como implementar um tipo de elemento de associação.  
  
## <a name="creating-a-new-binding"></a>Criar uma nova associação  
 Um elemento de associação criado pelo usuário pode ser usado de duas maneiras. A seção anterior ilustra o primeiro modo: por meio de uma associação personalizada. Uma associação personalizada permite que o usuário criar seu próprios associação com base em um conjunto arbitrário de elementos, incluindo aqueles criados pelo usuário de associação.  
  
 Se você usar a associação em mais de um aplicativo, crie sua própria associação e estender o <xref:System.ServiceModel.Channels.Binding>. Isso evita a criação manual de uma associação personalizada sempre que você deseja usá-lo. Uma associação definida pelo usuário permite definir o comportamento da associação e incluir elementos de associação definida pelo usuário. E é *empacotado previamente*: você não precisa recriar a associação toda vez que você usá-lo.  
  
 No mínimo, uma associação definida pelo usuário deve implementar o <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> método e o <xref:System.ServiceModel.Channels.Binding.Scheme%2A> propriedade.  
  
 O <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> método retorna um novo <xref:System.ServiceModel.Channels.BindingElementCollection> que contém os elementos de associação para a associação. A coleção é ordenada e deve conter os elementos de associação de protocolo primeiro, seguido pelo elemento de associação de codificação, seguido pelo elemento de associação de transporte. Ao usar o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] elementos de associação fornecido pelo sistema, você deve seguir o elemento de associação ordenação regras especificadas na [personalizado associações](../../../../docs/framework/wcf/extending/custom-bindings.md). Esta coleção nunca deve fazer referência a objetos referenciados dentro da classe de associação definida pelo usuário; Consequentemente, os autores de associação devem retornar um `Clone()` do <xref:System.ServiceModel.Channels.BindingElementCollection> em cada chamada para <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A>.  
  
 O <xref:System.ServiceModel.Channels.Binding.Scheme%2A> propriedade representa o esquema de URI para o protocolo de transporte em uso na associação. Por exemplo, o *WSHttpBinding* e *NetTcpBinding* retornar "http" e "NET" de seus respectivos <xref:System.ServiceModel.Channels.Binding.Scheme%2A> propriedades.  
  
 Para obter uma lista completa de opcionais métodos e propriedades para associações definidas pelo usuário, consulte <xref:System.ServiceModel.Channels.Binding>.  
  
### <a name="example"></a>Exemplo  
 Este exemplo implementa a associação de perfil em `SampleProfileUdpBinding`, que é derivado de <xref:System.ServiceModel.Channels.Binding>. O `SampleProfileUdpBinding` contém até quatro elementos de associação nele: um usuário criado `UdpTransportBindingElement`; e três fornecido pelo sistema: `TextMessageEncodingBindingElement`, `CompositeDuplexBindingElement`, e `ReliableSessionBindingElement`.  
  
```  
public override BindingElementCollection CreateBindingElements()  
{     
    BindingElementCollection bindingElements = new BindingElementCollection();  
    if (ReliableSessionEnabled)  
    {  
        bindingElements.Add(session);  
        bindingElements.Add(compositeDuplex);  
    }  
    bindingElements.Add(encoding);  
    bindingElements.Add(transport);  
    return bindingElements.Clone();  
}  
```  
  
## <a name="security-restrictions-with-duplex-contracts"></a>Restrições de segurança com contratos Duplex  
 Nem todos os elementos de associação são compatíveis entre si. Em particular, há algumas restrições sobre segurança de elementos de associação quando usado com contratos duplex.  
  
### <a name="one-shot-security"></a>Segurança da  
 Você pode implementar a segurança de "todos", onde todas as credenciais de segurança necessárias são enviadas em uma única mensagem, definindo o `negotiateServiceCredential` atributo o \<mensagem > elemento de configuração para `false`.  
  
 Autenticação única não funciona com contratos duplex.  
  
 Para contratos de solicitação-resposta da autenticação só funcionará se a pilha de associação abaixo do elemento de associação de segurança dá suporte à criação <xref:System.ServiceModel.Channels.IRequestChannel> ou <xref:System.ServiceModel.Channels.IRequestSessionChannel> instâncias.  
  
 Para contratos unidirecionais, da autenticação funciona se a pilha de associação abaixo do elemento de associação de segurança dá suporte à criação <xref:System.ServiceModel.Channels.IRequestChannel>, <xref:System.ServiceModel.Channels.IRequestSessionChannel>, <xref:System.ServiceModel.Channels.IOutputChannel> ou <xref:System.ServiceModel.Channels.IOutputSessionChannel> instâncias.  
  
### <a name="cookie-mode-security-context-tokens"></a>Tokens de contexto de segurança do modo de cookie  
 Tokens de contexto de segurança de modo de cookie não podem ser usados com contratos duplex.  
  
 Para contratos de solicitação-resposta, o contexto de segurança do modo de cookie tokens trabalho somente se a pilha de associação abaixo do elemento de associação de segurança dá suporte à criação <xref:System.ServiceModel.Channels.IRequestChannel> ou <xref:System.ServiceModel.Channels.IRequestSessionChannel> instâncias.  
  
 Para contratos unidirecionais, o contexto de segurança do modo de cookie tokens funciona se a pilha de associação abaixo do elemento de associação de segurança dá suporte à criação <xref:System.ServiceModel.Channels.IRequestChannel> ou <xref:System.ServiceModel.Channels.IRequestSessionChannel> instâncias.  
  
### <a name="session-mode-security-context-tokens"></a>Tokens de contexto de segurança do modo de sessão  
 Modo de sessão SCT funciona para contratos duplex se a pilha de associação abaixo do elemento de associação de segurança dá suporte à criação <xref:System.ServiceModel.Channels.IDuplexChannel> ou <xref:System.ServiceModel.Channels.IDuplexSessionChannel> instâncias.  
  
 Modo de sessão SCT funciona para se a pilha de associação abaixo do elemento de associação de segurança dá suporte à criação de contratos de solicitação-resposta <xref:System.ServiceModel.Channels.IDuplexChannel>, <xref:System.ServiceModel.Channels.IDuplexSessionChannel>, <xref:System.ServiceModel.Channels.IRequestChannel> ou <xref:System.ServiceModel.Channels.IRequestSessionChannel>, instâncias.  
  
 Modo de sessão SCT funciona para contratos de maneira 1 se a pilha de associação abaixo do elemento de associação de segurança dá suporte à criação <xref:System.ServiceModel.Channels.IDuplexChannel>, <xref:System.ServiceModel.Channels.IDuplexSessionChannel>, <xref:System.ServiceModel.Channels.IRequestChannel> ou <xref:System.ServiceModel.Channels.IRequestSessionChannel> instâncias.  
  
## <a name="deriving-from-a-standard-binding"></a>Derivando de uma associação padrão  
 Em vez de criar uma classe de associação totalmente nova, é possível estender uma das associações fornecidas pelo sistema existentes. Bem como no caso anterior, você deve substituir o <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> método e o <xref:System.ServiceModel.Channels.Binding.Scheme%2A> propriedade.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Channels.Binding>  
 [Associações personalizadas](../../../../docs/framework/wcf/extending/custom-bindings.md)
