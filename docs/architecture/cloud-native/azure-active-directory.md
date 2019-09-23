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
# <a name="azure-active-directory"></a><span data-ttu-id="3f04e-103">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="3f04e-103">Azure Active Directory</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="3f04e-104">O Microsoft Azure Active Directory (AD do Azure) oferece gerenciamento de identidade e acesso como um serviço.</span><span class="sxs-lookup"><span data-stu-id="3f04e-104">Microsoft Azure Active Directory (Azure AD) offers identity and access management as a service.</span></span> <span data-ttu-id="3f04e-105">Os clientes o utilizam para configurar e manter quem são os usuários, quais informações armazenar sobre eles, quem pode acessar essas informações, quem pode gerenciá-lo e quais aplicativos podem acessá-lo.</span><span class="sxs-lookup"><span data-stu-id="3f04e-105">Customers use it to configure and maintain who users are, what information to store about them, who can access that information, who can manage it, and what apps can access it.</span></span> <span data-ttu-id="3f04e-106">O AAD pode autenticar usuários para aplicativos configurados para usá-lo, fornecendo uma experiência de logon único (SSO).</span><span class="sxs-lookup"><span data-stu-id="3f04e-106">AAD can authenticate users for applications configured to use it, providing a single sign-on (SSO) experience.</span></span> <span data-ttu-id="3f04e-107">Ele pode ser usado sozinho ou ser integrado ao Windows AD em execução local.</span><span class="sxs-lookup"><span data-stu-id="3f04e-107">It can be used on its own or be integrated with Windows AD running on premises.</span></span>

<span data-ttu-id="3f04e-108">O Azure AD é criado para a nuvem.</span><span class="sxs-lookup"><span data-stu-id="3f04e-108">Azure AD is built for the cloud.</span></span> <span data-ttu-id="3f04e-109">É realmente uma solução de identidade nativa de nuvem que usa uma sintaxe API do Graph e OData baseada em REST para consultas, ao contrário do Windows AD, que usa LDAP.</span><span class="sxs-lookup"><span data-stu-id="3f04e-109">It's truly a cloud-native identity solution that uses a REST-based Graph API and OData syntax for queries, unlike Windows AD, which uses LDAP.</span></span> <span data-ttu-id="3f04e-110">No local Active Directory pode sincronizar os atributos de usuário para a nuvem usando os serviços de sincronização de identidade, permitindo que toda a autenticação ocorra na nuvem usando o Azure AD.</span><span class="sxs-lookup"><span data-stu-id="3f04e-110">On premises Active Directory can sync user attributes to the cloud using Identity Sync Services, allowing all authentication to take place in the cloud using Azure AD.</span></span> <span data-ttu-id="3f04e-111">Como alternativa, a autenticação pode ser configurada por meio do Connect para passar para o Active Directory local por meio do ADFS para ser concluída pelo Windows AD local.</span><span class="sxs-lookup"><span data-stu-id="3f04e-111">Alternately, authentication can be configured via Connect to pass back to local Active Directory via ADFS to be completed by Windows AD on premises.</span></span>

<span data-ttu-id="3f04e-112">O Azure AD dá suporte a telas de entrada da empresa, autenticação de várias fábricas e proxies de aplicativo baseados em nuvem que são usados para fornecer SSO para aplicativos hospedados localmente.</span><span class="sxs-lookup"><span data-stu-id="3f04e-112">Azure AD supports company branded sign-in screens, multi-factory authentication, and cloud-based application proxies that are used to provide SSO for applications hosted on premises.</span></span> <span data-ttu-id="3f04e-113">Ele oferece tipos diferentes de relatórios de segurança e recursos de alerta.</span><span class="sxs-lookup"><span data-stu-id="3f04e-113">It offers different kinds of security reporting and alert capabilities.</span></span>

## <a name="references"></a><span data-ttu-id="3f04e-114">Referências</span><span class="sxs-lookup"><span data-stu-id="3f04e-114">References</span></span>

- [<span data-ttu-id="3f04e-115">Plataforma de identidade da Microsoft</span><span class="sxs-lookup"><span data-stu-id="3f04e-115">Microsoft identity platform</span></span>](https://docs.microsoft.com/azure/active-directory/develop/)

>[!div class="step-by-step"]
><span data-ttu-id="3f04e-116">[Anterior](authentication-authorization.md)
>[Próximo](identity-server.md)</span><span class="sxs-lookup"><span data-stu-id="3f04e-116">[Previous](authentication-authorization.md)
[Next](identity-server.md)</span></span>
