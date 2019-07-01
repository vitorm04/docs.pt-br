---
title: Segurança de transporte de HTTP
ms.date: 03/30/2017
ms.assetid: d3439262-c58e-4d30-9f2b-a160170582bb
ms.openlocfilehash: 456df42848c009dcf42022ac674a1d27e5b33972
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2019
ms.locfileid: "67487025"
---
# <a name="http-transport-security"></a>Segurança de transporte de HTTP
Ao usar o HTTP como o transporte, a segurança é fornecida por uma implementação de Secure Sockets Layer (SSL). SSL é amplamente usado na Internet para autenticar um serviço para um cliente e, em seguida, para fornecer confidencialidade (criptografia) para o canal. Este tópico explica como o SSL funciona e como ele é implementado no Windows Communication Foundation (WCF).  
  
## <a name="basic-ssl"></a>Basic SSL  
 Como funciona o SSL é melhor explicada por meio de um cenário típico, nesse caso, site da Web de um banco. O site permite que o cliente faça logon com um nome de usuário e senha. Após ser autenticado, o usuário pode executar transações, como exibir saldos da conta, pagar contas e mover o dinheiro de uma conta para outra.  
  
 Quando um usuário pela primeira vez visita o site, o mecanismo SSL inicia uma série de negociações, chamado de um *handshake*, com cliente do usuário (neste caso, o Internet Explorer). Primeiro, o SSL autentica o site do banco para o cliente. Isso é uma etapa essencial porque os clientes primeiro devem saber que eles estão se comunicando com o site real e não uma falsificação que tenta seduzir digitando seu nome de usuário e senha. SSL faz essa autenticação usando um certificado SSL fornecido por uma autoridade confiável, como a VeriSign. A lógica funciona assim: VeriSign garante a identidade do site do banco. Como a VeriSign confia no Internet Explorer, o site é confiável. Se você quiser verificar com a VeriSign, você pode fazer então também clicando no logotipo VeriSign. Que apresenta uma instrução de autenticidade com a data de expiração e que ele é emitido para (o site do banco).  
  
 Para iniciar uma sessão segura, o cliente envia o equivalente a um "Olá" para o servidor, juntamente com uma lista de algoritmos criptográficos, ele pode usar para entrar, gerar hashes e criptografar e descriptografar com. Em resposta, o site envia de volta uma confirmação e sua escolha de um dos pacotes de algoritmos. Durante esse handshake inicial, ambas as partes enviarem e recebem valores de uso único. Um *nonce* é um dado gerado aleatoriamente que é usado, em combinação com a chave do site público, para criar um hash. Um *hash* é um novo número é derivado de dois números usando um algoritmo padrão, como o SHA1. (O cliente e o site também trocam mensagens para concordar com o algoritmo de hash que será usado). O hash é exclusivo e é usado somente para a sessão entre o cliente e o site para criptografar e descriptografar mensagens. Cliente e o serviço tem o nonce original e a chave do certificado público, portanto, ambos os lados podem gerar o mesmo hash. Portanto, o cliente valida o hash enviado pelo serviço (a) usando o acordado ao algoritmo para calcular o hash dos dados e (b) compará-lo com o hash enviado pelo serviço; Se os dois são iguais, o cliente tem garantia de que o hash não foram violado. O cliente pode, em seguida, usar o hash como uma chave para criptografar uma mensagem que contém outro novo hash. O serviço pode descriptografar a mensagem usando o hash e recuperar o hash do segundo ao último. As informações acumuladas (nonces, chave pública e outros dados) agora são conhecidas para ambos os lados e um hash final (ou a chave mestra) podem ser criada. Essa chave final é enviado criptografado usando o hash do próximo ao último. A chave mestra, em seguida, é usada para criptografar e descriptografar as mensagens para o restante da sessão. Como cliente e o serviço usam a mesma chave, isso também é chamado de um *chave de sessão*.  
  
 A chave de sessão também é caracterizada como uma chave simétrica ou um "segredo compartilhado". É importante ter uma chave simétrica, pois ele reduz a computação necessária por ambos os lados da transação. Se todas as mensagens exigiam um novo exchange de nonces e hashes, desempenho seria diminuir. Portanto, o objetivo final de SSL é usar uma chave simétrica que permite que as mensagens fluir livremente entre os dois lados com um grau maior de segurança e eficiência.  
  
 A descrição anterior é uma versão simplificada do que acontece, porque o protocolo pode variar de um site a site. Também é possível que o cliente e o site ambos geram nonces algoritmicamente são combinadas durante o handshake para adicionar mais complexidade e, portanto, proteção, o processo de troca de dados.  
  
### <a name="certificates-and-public-key-infrastructure"></a>Certificados e infraestrutura de chave pública  
 Durante o handshake, o serviço também envia seu certificado SSL para o cliente. O certificado contém informações, como data de expiração, emitindo a autoridade e identificador de URI do site (Uniform Resource). O cliente compara o URI para o URI, ele tinha originalmente contatado para garantir a correspondência e também verifica a data e a autoridade emissora.  
  
 Cada certificado tem duas chaves, uma chave privada e uma chave pública e os dois são conhecidos como uma *par de chaves do exchange*. Em suma, a chave privada conhecida apenas o proprietário do certificado enquanto a chave pública pode ser lida do certificado. Qualquer chave pode ser usada para criptografar ou descriptografar um resumo, hash, ou outra chave, mas somente como contrary operações. Por exemplo, se o cliente criptografa com a chave pública, somente o site pode descriptografar a mensagem usando a chave privada. Da mesma forma, se o site criptografa com a chave privada, o cliente pode descriptografar com a chave pública. Isso fornece garantia para o cliente que as mensagens estão sendo trocadas apenas com o detentor da chave privada porque apenas as mensagens criptografadas com a chave particular podem ser descriptografadas com a chave pública. O site terá certeza de que ele está trocando mensagens com um cliente que tenha criptografado usando a chave pública. Essa troca é segura somente para um handshake inicial, no entanto, razão pela qual muito mais é feito para criar a chave simétrica real. No entanto, todas as comunicações dependem do serviço tem um certificado SSL válido.  
  
## <a name="implementing-ssl-with-wcf"></a>Implementando o SSL com o WCF  
 Segurança de transporte HTTP (ou SSL) é fornecido externamente para o WCF. Você pode implementar o SSL em uma das duas maneiras; o fator decisivo é como o seu aplicativo está hospedado:  
  
- Se você estiver usando o Internet Information Services (IIS) do seu host do WCF, use a infraestrutura do IIS para configurar um serviço SSL.  
  
- Se você estiver criando um aplicativo WCF auto-hospedado, você pode associar um certificado SSL para o endereço usando a ferramenta HttpCfg.exe.  
  
### <a name="using-iis-for-transport-security"></a>Usando o IIS para segurança de transporte  
  
#### <a name="iis-70"></a>IIS 7.0  
 Para configurar o IIS 7.0 como um host protegido (usando SSL), consulte [Configurando Secure Sockets Layer no IIS 7.0](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc771438(v=ws.10)).  
  
Para configurar certificados para uso com o IIS 7.0, consulte [Configuring Server Certificates in IIS 7.0](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732230(v=ws.10)).  
  
#### <a name="iis-60"></a>IIS 6,0  
 Para configurar o IIS 6.0 como um host protegido (usando SSL), consulte [Configurando Secure Sockets Layer](https://go.microsoft.com/fwlink/?LinkId=88601).  
  
 Para configurar certificados para uso com o IIS 6.0, consulte [Certificates_IIS_SP1_Ops](https://go.microsoft.com/fwlink/?LinkId=88602).  
  
### <a name="using-httpcfg-for-ssl"></a>Usando HttpCfg para SSL  
 Se você estiver criando um aplicativo WCF auto-hospedado, baixe a ferramenta HttpCfg.exe, disponível na [site de ferramentas de suporte do Windows XP Service Pack 2](https://go.microsoft.com/fwlink/?LinkId=29002).  
  
 Para obter mais informações sobre como usar a ferramenta HttpCfg.exe para configurar uma porta com um certificado X.509, consulte [como: Configurar uma porta com um certificado SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).  
  
## <a name="see-also"></a>Consulte também

- [Segurança de transporte](../../../../docs/framework/wcf/feature-details/transport-security.md)
- [Segurança de mensagem](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)
