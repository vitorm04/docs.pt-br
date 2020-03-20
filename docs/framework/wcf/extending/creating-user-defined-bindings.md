---
title: Criando associações definidas pelo usuário
ms.date: 03/30/2017
helpviewer_keywords:
- user-defined bindings [WCF]
ms.assetid: c4960675-d701-4bc9-b400-36a752fdd08b
ms.openlocfilehash: 34100569dc5cd5a340abca66fedca40ba21c1e0b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185638"
---
# <a name="creating-user-defined-bindings"></a>Criando associações definidas pelo usuário
Existem várias maneiras de criar vinculações não fornecidas pelo sistema:  
  
- Crie uma vinculação personalizada, com base na <xref:System.ServiceModel.Channels.CustomBinding> classe, que é um recipiente que você preenche com elementos de ligação. A vinculação personalizada é então adicionada a um ponto final de serviço. Você pode criar a vinculação personalizada programática ou em um arquivo de configuração de aplicativo. Para usar um elemento de vinculação de um <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>arquivo de configuração de aplicativo, o elemento de vinculação deve estender . Para obter mais informações sobre vinculações <xref:System.ServiceModel.Channels.CustomBinding>personalizadas, consulte [Vinculações personalizadas](custom-bindings.md) e .  
  
- Você pode criar uma classe que deriva de uma vinculação padrão. Por exemplo, você pode <xref:System.ServiceModel.WSHttpBinding> derivar <xref:System.ServiceModel.Channels.CustomBinding.CreateBindingElements%2A> uma classe e substituir o método para obter os elementos de ligação e inserir um elemento de vinculação personalizado ou estabelecer um valor específico para a segurança.  
  
- Você pode criar <xref:System.ServiceModel.Channels.Binding> um novo tipo para controlar completamente toda a implementação de vinculação.  
  
## <a name="the-order-of-binding-elements"></a>A Ordem dos Elementos Vinculantes  
 Cada elemento de vinculação representa uma etapa de processamento ao enviar ou receber mensagens. Em tempo de execução, elementos de vinculação criam os canais e ouvintes necessários para construir pilhas de canais de saída e entrada.  
  
 Existem três tipos principais de elementos de ligação: Elementos de Ligação de Protocolo, Elementos de Enligação de Codificação e Elementos de Ligação de Transporte.  
  
 Elementos de vinculação de protocolo – Esses elementos representam etapas de processamento de nível superior que atuam nas mensagens. Canais e ouvintes criados por esses elementos de vinculação podem adicionar, remover ou modificar o conteúdo da mensagem. Uma dada vinculação pode ter um número arbitrário de elementos de ligação de protocolo, cada um herdando de <xref:System.ServiceModel.Channels.BindingElement>. A Windows Communication Foundation (WCF) inclui vários <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> elementos de ligação de protocolo, incluindo o e o <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.  
  
 Elemento de encodificação de encadernação – Esses elementos representam transformações entre uma mensagem e uma codificação pronta para transmissão no fio. As ligações típicas do WCF incluem exatamente um elemento de vinculação de codificação. Exemplos de elementos de <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>encodificação de vinculação incluem o , o <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>, e o <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>. Se um elemento de enligação de codificação não for especificado para uma vinculação, uma codificação padrão será usada. O padrão é texto quando o transporte é HTTP e binário de outra forma.  
  
 Elemento de ligação de transporte – Esses elementos representam a transmissão de uma mensagem de codificação em um protocolo de transporte. As ligações típicas do WCF incluem exatamente <xref:System.ServiceModel.Channels.TransportBindingElement>um elemento de ligação de transporte, que herda de . Exemplos de elementos de <xref:System.ServiceModel.Channels.TcpTransportBindingElement>ligação <xref:System.ServiceModel.Channels.HttpTransportBindingElement>de <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>transporte incluem o , o , e o .  
  
 Ao criar novas vinculações, a ordem dos elementos de ligação adicionados é importante. Sempre adicione elementos de vinculação na seguinte ordem:  
  
|Camada|Opções|Obrigatório|  
|-----------|-------------|--------------|  
|Fluxo de Transações|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement?displayProperty=nameWithType>|Não|  
|Confiabilidade|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement?displayProperty=nameWithType>|Não|  
|Segurança|<xref:System.ServiceModel.Channels.SecurityBindingElement?displayProperty=nameWithType>|Não|  
|Duplex composto|<xref:System.ServiceModel.Channels.CompositeDuplexBindingElement?displayProperty=nameWithType>|Não|  
|Codificação|Texto, Binário, MTOM, Personalizado|Sim\*|  
|Transporte|TCP, chamado Pipes, HTTP, HTTPS, MSMQ, Custom|Sim|  
  
\*Como uma codificação é necessária para cada vinculação, se uma codificação não for especificada, o WCF adiciona uma codificação padrão para você. O padrão é Texto/XML para os transportes HTTP e HTTPS e Binário de outra forma.  
  
## <a name="creating-a-new-binding-element"></a>Criando um novo elemento de vinculação  
 Além dos tipos derivados <xref:System.ServiceModel.Channels.BindingElement> do que são fornecidos pelo WCF, você pode criar seus próprios elementos de ligação. Isso permite que você personalize a forma como a pilha de amarras é <xref:System.ServiceModel.Channels.BindingElement> criada e os componentes que vão nele criando o seu próprio que pode ser composto com os outros tipos fornecidos pelo sistema na pilha.  
  
 Por exemplo, se `LoggingBindingElement` você implementar um que fornece a capacidade de registrar a mensagem em um banco de dados, você deve colocá-la acima de um canal de transporte na pilha de canais. Neste caso, o aplicativo cria uma `LoggingBindingElement` vinculação personalizada que compôs o com `TcpTransportBindingElement`, como no exemplo a seguir.  
  
```csharp  
Binding customBinding = new CustomBinding(  
  new LoggingBindingElement(),
  new TcpTransportBindingElement()  
);  
```  
  
 A forma como você escreve seu novo elemento de vinculação depende de sua funcionalidade exata. Uma das amostras, [Transport: UDP](../samples/transport-udp.md), fornece uma descrição detalhada de como implementar um tipo de elemento de ligação.  
  
## <a name="creating-a-new-binding"></a>Criando uma nova vinculação  
 Um elemento de vinculação criado pelo usuário pode ser usado de duas maneiras. A seção anterior ilustra a primeira maneira: através de uma vinculação personalizada. Uma vinculação personalizada permite que o usuário crie sua própria vinculação com base em um conjunto arbitrário de elementos de vinculação, incluindo os criados pelo usuário.  
  
 Se você usar a vinculação em mais de um <xref:System.ServiceModel.Channels.Binding>aplicativo, crie sua própria vinculação e amplie o . Isso evita criar manualmente uma vinculação personalizada toda vez que você quiser usá-la. Uma vinculação definida pelo usuário permite definir o comportamento da vinculação e incluir elementos de vinculação definidos pelo usuário. E é *pré-embalado:* você não precisa reconstruir a ligação toda vez que usá-la.  
  
 No mínimo, uma vinculação definida <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> pelo usuário <xref:System.ServiceModel.Channels.Binding.Scheme%2A> deve implementar o método e a propriedade.  
  
 O <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> método retorna <xref:System.ServiceModel.Channels.BindingElementCollection> um novo que contém os elementos de ligação para a ligação. A coleta é ordenada e deve conter os elementos de ligação do protocolo primeiro, seguido do elemento de enligação de codificação, seguido pelo elemento de ligação de transporte. Ao usar os elementos de vinculação fornecidos pelo sistema WCF, você deve seguir as regras de ordenação de elementos vinculantes especificadas em [Vinculações Personalizadas](custom-bindings.md). Esta coleção nunca deve referenciar objetos referenciados na classe de vinculação definida pelo usuário; consequentemente, os autores `Clone()` vinculantes <xref:System.ServiceModel.Channels.BindingElementCollection> devem retornar <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A>um dos em cada chamada para .  
  
 A <xref:System.ServiceModel.Channels.Binding.Scheme%2A> propriedade representa o regime URI para o protocolo de transporte em uso na vinculação. Por exemplo, o *WSHttpBinding* e o *NetTcpBinding* retornam "http" e <xref:System.ServiceModel.Channels.Binding.Scheme%2A> "net.tcp" de suas respectivas propriedades.  
  
 Para obter uma lista completa de métodos e propriedades <xref:System.ServiceModel.Channels.Binding>opcionais para vinculações definidas pelo usuário, consulte .  
  
### <a name="example"></a>Exemplo  
 Este exemplo implementa `SampleProfileUdpBinding`a vinculação <xref:System.ServiceModel.Channels.Binding>de perfil em , que deriva de . O `SampleProfileUdpBinding` contém até quatro elementos de ligação `UdpTransportBindingElement`dentro dele: um criado pelo usuário; e três sistemas fornecidos: `TextMessageEncodingBindingElement`, `CompositeDuplexBindingElement`e `ReliableSessionBindingElement`.  
  
```csharp
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
  
## <a name="security-restrictions-with-duplex-contracts"></a>Restrições de segurança com contratos duplex  
 Nem todos os elementos de ligação são compatíveis uns com os outros. Em particular, existem algumas restrições aos elementos de vinculação de segurança quando usados com contratos duplex.  
  
### <a name="one-shot-security"></a>Segurança de um tiro  
 Você pode implementar a segurança "one-shot", onde todas as credenciais de `negotiateServiceCredential` segurança \<necessárias são `false`enviadas em uma única mensagem, definindo o atributo do elemento de configuração> de mensagem para .  
  
 A autenticação de um tiro não funciona com contratos duplex.  
  
 Para contratos de solicitação de resposta, a autenticação de um tiro só <xref:System.ServiceModel.Channels.IRequestChannel> <xref:System.ServiceModel.Channels.IRequestSessionChannel> funciona se a pilha de vinculação abaixo do elemento de vinculação de segurança suportar a criação ou instâncias.  
  
 Para contratos unidirecionais, a autenticação de um tiro só funciona <xref:System.ServiceModel.Channels.IRequestChannel>se <xref:System.ServiceModel.Channels.IRequestSessionChannel> <xref:System.ServiceModel.Channels.IOutputChannel> a <xref:System.ServiceModel.Channels.IOutputSessionChannel> pilha de vinculação abaixo do elemento de vinculação de segurança for suporte a criação ou instâncias.  
  
### <a name="cookie-mode-security-context-tokens"></a>Tokens de contexto de segurança no modo de cookie  
 Os tokens de contexto de segurança do modo cookie não podem ser usados com contratos duplex.  
  
 Para contratos de solicitação de resposta, os tokens de contexto de segurança no <xref:System.ServiceModel.Channels.IRequestChannel> <xref:System.ServiceModel.Channels.IRequestSessionChannel> modo de cookies funcionam somente se a pilha de vinculação abaixo do elemento de vinculação de segurança for suporte à criação ou instâncias.  
  
 Para contratos unidirecionais, os tokens de contexto de segurança no modo <xref:System.ServiceModel.Channels.IRequestChannel> de <xref:System.ServiceModel.Channels.IRequestSessionChannel> cookies funcionam se a pilha de vinculação abaixo do elemento de vinculação de segurança for suporte à criação ou instâncias.  
  
### <a name="session-mode-security-context-tokens"></a>Tokens de contexto de segurança em modo de sessão  
 Modo de sessão O SCT funciona para contratos duplex se <xref:System.ServiceModel.Channels.IDuplexChannel> <xref:System.ServiceModel.Channels.IDuplexSessionChannel> a pilha de vinculação abaixo do elemento de vinculação de segurança suportar a criação ou instâncias.  
  
 Modo de sessão O SCT funciona para contratos de solicitação e <xref:System.ServiceModel.Channels.IDuplexChannel> <xref:System.ServiceModel.Channels.IDuplexSessionChannel>resposta <xref:System.ServiceModel.Channels.IRequestChannel> <xref:System.ServiceModel.Channels.IRequestSessionChannel>se a pilha de vinculação abaixo do elemento de vinculação de segurança suportar a criação de instâncias ou instâncias.  
  
 Modo de sessão O SCT funciona para contratos de 1 via <xref:System.ServiceModel.Channels.IDuplexChannel> <xref:System.ServiceModel.Channels.IDuplexSessionChannel>se <xref:System.ServiceModel.Channels.IRequestChannel> <xref:System.ServiceModel.Channels.IRequestSessionChannel> a pilha de vinculação abaixo do elemento de vinculação de segurança for suporte a criação ou instâncias.  
  
## <a name="deriving-from-a-standard-binding"></a>Derivando de uma vinculação padrão  
 Em vez de criar uma classe de vinculação totalmente nova, pode ser possível estender uma das vinculações fornecidas pelo sistema existentes. Assim como no caso anterior, <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> você deve <xref:System.ServiceModel.Channels.Binding.Scheme%2A> substituir o método e a propriedade.  
  
## <a name="see-also"></a>Confira também

- <xref:System.ServiceModel.Channels.Binding>
- [Associações personalizadas](custom-bindings.md)
