---
title: Índice de exemplos de código do WIF
ms.date: 03/30/2017
ms.assetid: 6711f01a-4743-43ce-95ab-5e2302a363ea
author: BrucePerlerMS
ms.openlocfilehash: b1c875f6c49a3097a75f88b1c25555fd7e891b1f
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57356592"
---
# <a name="wif-code-sample-index"></a>Índice de exemplos de código do WIF

Veja a seguir amostras de código do Windows Identity Foundation 4.5:

- [ClaimsAwareWebApp](https://go.microsoft.com/fwlink/?LinkID=248405) – essa amostra apresenta o uso básico da externalização de autenticação (para o Serviço de Token de Segurança de teste local por meio da Ferramenta de Identidade e Acesso para o Visual Studio 11) em um aplicativo ASP.NET clássico (em vez de um site).

- [ClaimsAwareWebService](https://go.microsoft.com/fwlink/?LinkID=248406) – essa amostra apresenta o uso básico da externalização de autenticação em um serviço WCF clássico.

- [ClaimsAwareMvcApplication](https://go.microsoft.com/fwlink/?LinkID=248407) – essa amostra explica como integrar o WIF ao MVC, incluindo proteção não abrangente e um código que respeita o redirecionamento da autenticação de formulários fora do controlador LogOn.

- [ClaimsAwareWebFarm](https://go.microsoft.com/fwlink/?LinkID=248408) – essa amostra apresenta um cache de sessão pronto para o farm (em vez de um tokenreplycache), para que você possa usar sessões por referência, em vez de trocar cookies grandes. Ela também demonstra uma maneira mais fácil de proteger cookies em um farm.

- [ClaimsAwareFormsAuthentication](https://go.microsoft.com/fwlink/?LinkID=248409) – essa amostra muito simples explica que, no .NET 4.5, as declarações são obtidas nas entidades de segurança, independentemente de como os usuários são autenticados.

- [ClaimsBasedAuthorization](https://go.microsoft.com/fwlink/?LinkID=248410)– essa amostra explica como usar a classe ClaimsAuthorizationManager e o ClaimsAuthorizationModule para aplicar suas próprias políticas de autorização.

- [FederationMetadata](https://go.microsoft.com/fwlink/?LinkID=248411) – essa amostra apresenta a geração dinâmica (em um STS personalizado) e o consumo dinâmico (em um aplicativo de terceira parte confiável) de documentos de metadados.

- [CustomToken](https://go.microsoft.com/fwlink/?LinkID=248412) – essa amostra explica como criar um tipo de token SWT (Token Web Simples) personalizado.

## <a name="see-also"></a>Consulte também

- [Windows Identity Foundation](../../../docs/framework/security/index.md)
