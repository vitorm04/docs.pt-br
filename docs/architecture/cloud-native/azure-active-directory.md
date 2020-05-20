---
title: Azure Active Directory
description: Arquitetando aplicativos .NET nativos da nuvem para o Azure | Azure Active Directory
ms.date: 06/30/2019
ms.openlocfilehash: 03f5ea8e84bc3c4a2a88a63d4b109aabf0c64f36
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614273"
---
# <a name="azure-active-directory"></a>Active Directory do Azure

O Microsoft Azure Active Directory (AD do Azure) oferece gerenciamento de identidade e acesso como um serviço. Os clientes o utilizam para configurar e manter quem são os usuários, quais informações armazenar sobre eles, quem pode acessar essas informações, quem pode gerenciá-lo e quais aplicativos podem acessá-lo. O AAD pode autenticar usuários para aplicativos configurados para usá-lo, fornecendo uma experiência de logon único (SSO). Ele pode ser usado sozinho ou ser integrado ao Windows AD em execução local.

O Azure AD é criado para a nuvem. É realmente uma solução de identidade nativa de nuvem que usa uma sintaxe API do Graph e OData baseada em REST para consultas, ao contrário do Windows AD, que usa LDAP. No local Active Directory pode sincronizar os atributos de usuário para a nuvem usando os serviços de sincronização de identidade, permitindo que toda a autenticação ocorra na nuvem usando o Azure AD. Como alternativa, a autenticação pode ser configurada por meio do Connect para passar para o Active Directory local por meio do ADFS para ser concluída pelo Windows AD local.

O Azure AD dá suporte a telas de entrada da empresa, autenticação de várias fábricas e proxies de aplicativo baseados em nuvem que são usados para fornecer SSO para aplicativos hospedados localmente. Ele oferece tipos diferentes de relatórios de segurança e recursos de alerta.

## <a name="references"></a>Referências

- [Plataforma de identidade da Microsoft](https://docs.microsoft.com/azure/active-directory/develop/)

>[!div class="step-by-step"]
>[Anterior](authentication-authorization.md) 
> [Avançar](identity-server.md)
