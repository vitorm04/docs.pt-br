---
title: Ferramenta de Identidade e Acesso para o Visual Studio 2012
ms.date: 03/30/2017
ms.assetid: 87b8f8f2-4074-44fd-9fd6-08278e877390
author: BrucePerlerMS
ms.openlocfilehash: a1b5456f9081d807a3c9e29e1010cbfbf91e637f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54678545"
---
# <a name="identity-and-access-tool-for-visual-studio-2012"></a>Ferramenta de Identidade e Acesso para o Visual Studio 2012
Este tópico descreve a nova Ferramenta de Identidade e Acesso para o Visual Studio 11. Você pode baixar essa ferramenta da seguinte URL: [ https://go.microsoft.com/fwlink/?LinkID=245849 ](https://go.microsoft.com/fwlink/?LinkID=245849) ou diretamente do Visual Studio 11 pesquisando por "identidade" diretamente no Gerenciador de extensões.  
  
 A Ferramenta de Identidade e Acesso para o Visual Studio 11 fornece uma experiência de tempo de desenvolvimento drasticamente simplificada com os seguintes destaques:  
  
-   Usando a nova ferramenta, você pode desenvolver usando tipos de projeto de aplicativos Web e o IIS Express como alvo.  
  
-   Diferente da autenticação somente de proteção ampla, com a nova ferramenta, você pode especificar sua página de descoberta do realm/controlador inicial local (ou qualquer outro ponto de extremidade que trata a experiência de autenticação em seu aplicativo) e o WIF configurará todas as solicitações não autenticadas para irem para lá, em vez de redirecioná-las ao STS.  
  
-   A ferramenta inclui um STS (Serviço de Token de Segurança) de teste que é executado no computador local quando você inicia uma sessão de depuração. Consequentemente, você não precisa criar projetos STS personalizados e ajustá-los para obter as declarações necessárias para testar seus aplicativos. Os tipos e os valores das declarações são completamente personalizáveis.  
  
-   Você pode modificar as configurações comuns diretamente na interface de usuário da ferramenta, sem precisar editar o web.config.  
  
-   Você pode estabelecer federação com o Serviços de Federação do Active Directory (AD FS) 2.0 (ou outros provedores de WS-Federation) em uma única tela.  
  
-   A ferramenta usa os recursos do Windows Azure Access Control Service (ACS) com uma lista simples de caixas de seleção para todos os provedores de identidade que você deseja usar: Facebook, Google, Live ID, Yahoo!, qualquer provedor OpenID e qualquer provedor de WS-Federation. Selecione seus provedores de identidade, clique em OK e pressione F5. Seu aplicativo e o ACS serão configurados automaticamente e seu aplicativo de teste será baseado no ACS.  
  
## <a name="see-also"></a>Consulte também
- [Recursos do WIF](../../../docs/framework/security/wif-features.md)
