---
title: Azure Active Directory
description: Arquitetando aplicativos .NET nativos da nuvem para o Azure | Azure Active Directory
ms.date: 06/30/2019
ms.openlocfilehash: 207043507a9052c47683383a98cef6417a1a2740
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183689"
---
# <a name="azure-active-directory"></a>Azure Active Directory

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

O Microsoft Azure Active Directory (AD do Azure) oferece gerenciamento de identidade e acesso como um serviço. Os clientes o utilizam para configurar e manter quem são os usuários, quais informações armazenar sobre eles, quem pode acessar essas informações, quem pode gerenciá-lo e quais aplicativos podem acessá-lo. O AAD pode autenticar usuários para aplicativos configurados para usá-lo, fornecendo uma experiência de logon único (SSO). Ele pode ser usado sozinho ou ser integrado ao Windows AD em execução local.

O Azure AD é criado para a nuvem. É realmente uma solução de identidade nativa de nuvem que usa uma sintaxe API do Graph e OData baseada em REST para consultas, ao contrário do Windows AD, que usa LDAP. No local Active Directory pode sincronizar os atributos de usuário para a nuvem usando os serviços de sincronização de identidade, permitindo que toda a autenticação ocorra na nuvem usando o Azure AD. Como alternativa, a autenticação pode ser configurada por meio do Connect para passar para o Active Directory local por meio do ADFS para ser concluída pelo Windows AD local.

O Azure AD dá suporte a telas de entrada da empresa, autenticação de várias fábricas e proxies de aplicativo baseados em nuvem que são usados para fornecer SSO para aplicativos hospedados localmente. Ele oferece tipos diferentes de relatórios de segurança e recursos de alerta.

## <a name="references"></a>Referências

- [Plataforma de identidade da Microsoft](https://docs.microsoft.com/azure/active-directory/develop/)

>[!div class="step-by-step"]
>[Anterior](authentication-authorization.md)
>[Próximo](identity-server.md)
