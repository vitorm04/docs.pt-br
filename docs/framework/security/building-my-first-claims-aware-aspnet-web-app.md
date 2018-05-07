---
title: Criando meu primeiro aplicativo Web ASP.NET baseado em declarações
ms.date: 03/30/2017
ms.assetid: 3ee8ee7f-caba-4267-9343-e313fae2876d
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 7e36ec5b824f60057ce7b1f18c695607cf9b88a3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="building-my-first-claims-aware-aspnet-web-application"></a>Criando meu primeiro aplicativo Web ASP.NET baseado em declarações
## <a name="applies-to"></a>Aplica-se a  
  
-   Windows Identity Foundation (WIF)  
  
-   ASP.NET  
  
 Este tópico descreve o cenário da criação de aplicativos Web ASP.NET com reconhecimento de declarações usando o WIF. Geralmente há três participantes em um cenário de aplicativo com reconhecimento de declarações: o aplicativo em si, o usuário final e o STS (Serviço de Token de Segurança). A figura a seguir descreve esse cenário:  
  
 ![Aplicativo Web básico do WIF](../../../docs/framework/security/media/wifbasicwebapp.gif "WIFBasicWebApp")  
  
1.  O aplicativo com reconhecimento de declarações usa o WIF para identificar solicitações não autenticadas e redirecioná-las ao STS.  
  
2.  O usuário final fornece credenciais ao STS e, após a autenticação bem-sucedida, ele recebe um token do STS.  
  
3.  O usuário é redirecionado do STS ao aplicativo com reconhecimento de declarações com o token emitido pelo STS na solicitação.  
  
4.  O aplicativo com reconhecimento de declarações é configurado para usar o STS e os tokens que ele emite. O aplicativo com reconhecimento de declarações usa o WIF para validar o token e analisá-lo. Os desenvolvedores usam a API e os tipos do WIF, por exemplo, **ClaimsPrincpal**, apropriados para as necessidades do aplicativo, como implementar a autorização para ele.  
  
 A partir do .NET 4.5, o WIF faz parte do pacote do .NET Framework. Ter as classes do WIF diretamente disponíveis no Framework permite uma integração muito mais profunda da identidade baseada em declarações no .NET, facilitando o uso de declarações. Com o WIF 4.5, você não precisa instalar os componentes fora da banda para começar a desenvolver aplicativos Web com reconhecimento de declarações. As classes WIF agora são difundidas por vários assemblies, sendo os principais System.Security.Claims, System.IdentityModel e System.IdentityModel.Services.  
  
 STS é um serviço que emite tokens após a autenticação bem-sucedida. A Microsoft oferece dois STSs padrão do setor:  
  
-   [Serviços de Federação do Active Directory (AD FS) 2.0](http://go.microsoft.com/fwlink/?LinkID=247516) (http://go.microsoft.com/fwlink/?LinkID=247516)  
  
-   [Windows Azure Access Control Service (ACS)](http://go.microsoft.com/fwlink/?LinkID=247517) (http://go.microsoft.com/fwlink/?LinkID=247517).  
  
 O AD FS 2.0 faz parte do Windows Server R2 e pode ser usado como um STS para cenários locais. O ACS é um serviço de nuvem oferecido como parte da Plataforma Microsoft Azure. Para fins de testes ou educativos, você também pode usar outros STSs para criar seus aplicativos com reconhecimento de reivindicações. Por exemplo, você pode usar o STS de desenvolvimento Local que faz parte do [ferramenta de identidade e acesso para o Visual Studio](http://go.microsoft.com/fwlink/?LinkID=245849) (http://go.microsoft.com/fwlink/?LinkID=245849) que está disponível gratuitamente on-line.  
  
 Para criar seu primeiro aplicativo ASP.NET com reconhecimento de declarações usando o WIF, siga as instruções em uma destas referências:  
  
-   [Como criar um aplicativo Web ASP.NET MVC com reconhecimento de declarações usando WIF](../../../docs/framework/security/how-to-build-claims-aware-aspnet-mvc-web-app-using-wif.md)  
  
-   [Como criar um aplicativo Web Forms do ASP.NET com reconhecimento de declarações usando WIF](../../../docs/framework/security/how-to-build-claims-aware-aspnet-web-forms-app-using-wif.md)  
  
-   [Como criar um aplicativo ASP.NET com reconhecimento de declarações usando a autenticação baseada em formulários](../../../docs/framework/security/claims-aware-aspnet-app-forms-authentication.md)  
  
## <a name="see-also"></a>Consulte também  
 [Introdução ao WIF](../../../docs/framework/security/getting-started-with-wif.md)
