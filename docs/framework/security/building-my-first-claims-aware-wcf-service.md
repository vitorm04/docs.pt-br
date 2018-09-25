---
title: Criando meu primeiro serviço WCF baseado em declarações
ms.date: 03/30/2017
ms.assetid: e0e6d091-9a97-4888-8f2c-cbcee42d90ee
author: BrucePerlerMS
ms.openlocfilehash: e6324087afa62f276766c733284dc69e425b89bc
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47078507"
---
# <a name="building-my-first-claims-aware-wcf-service"></a>Criando meu primeiro serviço WCF baseado em declarações
## <a name="applies-to"></a>Aplica-se a  
  
-   Windows Identity Foundation (WIF)  
  
-   Windows Communication Foundation (WCF)  
  
## <a name="overview"></a>Visão geral  
 Este tópico descreve o cenário da criação de serviços WCF com reconhecimento de declarações usando o WIF. Geralmente há três participantes em um cenário de serviço Web com reconhecimento de declarações: o serviço Web em si, o usuário final e o STS (Serviço de Token de Segurança). A figura a seguir descreve esse cenário:  
  
 ![Serviço WCF básico baseado em declarações do WIF](../../../docs/framework/security/media/wifbasicclaimsawarewcfservice.gif "WIFBasicClaimsAwareWCFService")  
  
1.  O cliente do serviço WCF (às vezes chamado de agente) usa o WIF para enviar credenciais ao STS e, após a autenticação bem-sucedida, o agente receberá um token do STS.  
  
2.  O agente envia esse token emitido pelo STS para o serviço WCF.  
  
3.  O serviço WCF com reconhecimento de declarações é configurado para usar o STS e os tokens que ele emite. O serviço WCF com reconhecimento de declarações usa o WIF para validar o token e analisá-lo. Os desenvolvedores usam a API e os tipos do WIF, por exemplo, **ClaimsPrincipal**, apropriados para as necessidades do aplicativo, como implementar a autorização para ele.  
  
 A partir do .NET 4.5, o WIF faz parte do pacote do .NET Framework. Ter as classes do WIF diretamente disponíveis no Framework permite uma integração muito mais profunda da identidade baseada em declarações no .NET, facilitando o uso de declarações. Com o WIF 4.5, você não precisa instalar os componentes fora da banda para começar a desenvolver aplicativos Web com reconhecimento de declarações. As classes WIF agora são difundidas por vários assemblies, sendo os principais System.Security.Claims, System.IdentityModel e System.IdentityModel.Services.  
  
 STS é um serviço que emite tokens após a autenticação bem-sucedida. A Microsoft oferece dois STSs padrão do setor:  
  
-   [Serviços de Federação do Active Directory (AD FS) 2.0](https://go.microsoft.com/fwlink/?LinkID=247516)
  
-   [Windows Azure Access Control Service (ACS)](https://go.microsoft.com/fwlink/?LinkID=247517)
  
 O AD FS 2.0 faz parte do Windows Server R2 e pode ser usado como um STS para cenários locais. O Controle de Acesso do Azure Active Directory (também conhecido como Serviço de Controle de Acesso ou ACS) é um serviço de nuvem, oferecido como parte do Microsoft Azure. Para fins de testes ou educativos, você também pode usar outros STSs para criar seus aplicativos com reconhecimento de reivindicações. Por exemplo, você pode usar o STS de desenvolvimento Local que faz parte do [ferramenta de identidade e acesso para o Visual Studio](https://go.microsoft.com/fwlink/?LinkID=245849) que está disponível online gratuitamente.  
  
 Para criar seu primeiro serviço WCF com reconhecimento de declarações usando o WIF, consulte [How To: habilitar o WIF para um aplicativo de serviço Web WCF](../../../docs/framework/security/how-to-enable-wif-for-a-wcf-web-service-application.md).
  
## <a name="see-also"></a>Consulte também  
 [Introdução ao WIF](../../../docs/framework/security/getting-started-with-wif.md)
