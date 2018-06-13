---
title: Segurança de transporte de HTTP
ms.date: 03/30/2017
ms.assetid: d3439262-c58e-4d30-9f2b-a160170582bb
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: cc284f82f974d9b34ff1cf6732d2ee7b95528c44
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33495916"
---
# <a name="http-transport-security"></a>Segurança de transporte de HTTP
Ao usar o HTTP como o transporte, segurança é fornecida por uma implementação de Secure Sockets Layer (SSL). SSL é amplamente usado na Internet para autenticar um serviço para um cliente e, em seguida, para fornecer confidencialidade (criptografia) para o canal. Este tópico explica como o SSL funciona e como ele é implementado no Windows Communication Foundation (WCF).  
  
## <a name="basic-ssl"></a>SSL básico  
 Como o SSL funciona é melhor explicadas por meio de um cenário típico, nesse caso, site do banco. O site permite que um cliente fazer logon com um nome de usuário e senha. Após ser autenticado, o usuário pode executar transações, como exibir os saldos de conta, pagar contas e mover dinheiro de uma conta para outra.  
  
 Quando um usuário acessa primeiro o site, o mecanismo SSL começa uma série de negociações, chamado de um *handshake*, com o cliente do usuário (no caso, Internet Explorer). Primeiro, o SSL autentica o site do banco para o cliente. Isso é uma etapa essencial porque os clientes primeiro devem saber que eles estão se comunicando com o site atual e não um falso que tenta atrai-los digitando seu nome de usuário e senha. SSL faz essa autenticação usando um certificado SSL fornecido por uma autoridade confiável, como a VeriSign. A lógica é a seguinte: VeriSign garante a identidade do site bank. Como Internet Explorer confia VeriSign, o site é confiável. Se você quiser verificar com a VeriSign, você pode fazer mesmo clicando no logotipo VeriSign. Que apresenta uma instrução de autenticidade com a data de validade e que é emitido para (o site do banco).  
  
 Para iniciar uma sessão segura, o cliente envia o equivalente de "Olá" para o servidor junto com uma lista de algoritmos criptográficos, ele pode usar para entrar, gerar hashes e criptografar e descriptografar com. Em resposta, o site envia de volta um reconhecimento e sua escolha de um dos pacotes de algoritmos. Durante o handshake neste inicial, ambas as partes enviar e recebem valores de uso único. Um *nonce* é um dado gerado aleatoriamente que é usado, em combinação com a chave pública do site para criar um hash. Um *hash* é um novo número que é derivado de dois números usando um algoritmo padrão, como SHA1. (O cliente e o site também trocam mensagens concordar qual algoritmo de hash a ser usado). O hash é exclusivo e é usado somente para a sessão entre o cliente e o site para criptografar e descriptografar mensagens. Cliente e o serviço tem o nonce original e a chave pública de certificado, portanto, ambos os lados podem gerar o mesmo hash. Portanto, o cliente validará o hash enviado pelo serviço (a) usando combinado ao algoritmo para calcular o hash dos dados, e (b) comparando-a com o hash enviado pelo serviço; Se os dois são iguais, o cliente tem garantia de que o hash não foram violado. O cliente pode, em seguida, usar o hash como uma chave para criptografar uma mensagem que contém outro novo hash. O serviço pode descriptografar a mensagem usando o hash e recuperar o hash de segundo para o final. As informações acumuladas (valores de uso único, chave pública e outros dados) agora são conhecidas em ambos os lados, e um hash final (ou a chave mestra) podem ser criada. Essa chave final é enviada criptografada usando o hash do próximo ao último. A chave mestra, em seguida, é usada para criptografar e descriptografar mensagens para a redefinição da sessão. Como cliente e serviço usam a mesma chave, isso também é chamado um *chave de sessão*.  
  
 A chave de sessão também é caracterizada como uma chave simétrica ou um "segredo compartilhado". É importante ter uma chave simétrica, pois reduz a computação necessária para ambos os lados da transação. Se cada mensagem exigia um novo exchange de valores de uso único e hashes, desempenho seria diminuir. Portanto, o objetivo final de SSL é usar uma chave simétrica que permite que as mensagens fluxo livremente entre os dois lados com um grau maior de segurança e eficiência.  
  
 A descrição anterior é uma versão simplificada do que acontece, como o protocolo pode variar de um site a site. Também é possível que o cliente e o site ambos geram momentos maneira algorítmica são combinados durante o handshake para adicionar mais complexidade e, portanto, proteção, o processo de troca de dados.  
  
### <a name="certificates-and-public-key-infrastructure"></a>Certificados e infraestrutura de chave pública  
 Durante o handshake, o serviço também envia seu certificado SSL para o cliente. O certificado contém informações, como a data de validade, emitindo autoridade e identificador de URI do site (Uniform Resource). O cliente compara o URI para o URI que ele tinha originalmente contatado para garantir uma correspondência e também verifica a data e a autoridade emissora.  
  
 Cada certificado tem duas chaves, uma chave privada e uma chave pública e os dois são conhecidos como um *par de chaves do exchange*. Em suma, a chave privada é conhecida somente para o proprietário do certificado, enquanto a chave pública é legível do certificado. A chave pode ser usada para criptografar ou descriptografar um digest, hash, ou outra chave, mas apenas como contrary operações. Por exemplo, se o cliente criptografa com a chave pública, somente o site pode descriptografar a mensagem usando a chave privada. Da mesma forma, se o site criptografa com a chave privada, o cliente pode descriptografar com a chave pública. Isso fornece garantia ao cliente que as mensagens são troca somente com o detentor da chave privada porque somente mensagens criptografadas com a chave privada podem ser descriptografadas com a chave pública. O site terá certeza de que ele é trocar mensagens com um cliente que foi criptografada usando a chave pública. Essa troca é segura somente para um handshake inicial, no entanto, que é por isso é feito muito mais para criar a chave simétrica real. No entanto, todas as comunicações dependem do serviço tem um certificado SSL válido.  
  
## <a name="implementing-ssl-with-wcf"></a>Implementando o SSL com o WCF  
 Segurança de transporte HTTP (ou SSL) é fornecido externamente para o WCF. Você pode implementar o SSL de uma das duas maneiras; o fator decisivo é como o aplicativo está hospedado:  
  
-   Se você estiver usando o Internet Information Services (IIS) do seu host WCF, use a infraestrutura do IIS para configurar um serviço SSL.  
  
-   Se você estiver criando um aplicativo WCF auto-hospedado, você pode associar um certificado SSL para o endereço usando a ferramenta HttpCfg.exe.  
  
### <a name="using-iis-for-transport-security"></a>Usando o IIS para segurança de transporte  
  
#### <a name="iis-70"></a>IIS 7.0  
 Para configurar [!INCLUDE[iisver](../../../../includes/iisver-md.md)] como um host protegido (usando SSL), consulte [IIS 7.0 Beta: Configurando Secure Sockets Layer no IIS 7.0](http://go.microsoft.com/fwlink/?LinkId=88600).  
  
 Configurar certificados para uso com [!INCLUDE[iisver](../../../../includes/iisver-md.md)], consulte [IIS 7.0 Beta: Configurando certificados de servidor no IIS 7.0](http://go.microsoft.com/fwlink/?LinkID=88595).  
  
#### <a name="iis-60"></a>IIS 6,0  
 Para configurar [!INCLUDE[iis601](../../../../includes/iis601-md.md)] como um host protegido (usando SSL), consulte [Configurando Secure Sockets Layer](http://go.microsoft.com/fwlink/?LinkId=88601).  
  
 Configurar certificados para uso com [!INCLUDE[iis601](../../../../includes/iis601-md.md)], consulte [Certificates_IIS_SP1_Ops](http://go.microsoft.com/fwlink/?LinkId=88602).  
  
### <a name="using-httpcfg-for-ssl"></a>Usar HttpCfg para SSL  
 Se você estiver criando um aplicativo WCF auto-hospedado, baixe a ferramenta HttpCfg.exe, disponível no [site de ferramentas de suporte do Windows XP Service Pack 2](http://go.microsoft.com/fwlink/?LinkId=29002).  
  
 Para obter mais informações sobre como usar a ferramenta HttpCfg.exe para configurar uma porta com um certificado x. 509, consulte [como: configurar uma porta com um certificado SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).  
  
## <a name="see-also"></a>Consulte também  
 [Segurança de transporte](../../../../docs/framework/wcf/feature-details/transport-security.md)  
 [Segurança de mensagem](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)
