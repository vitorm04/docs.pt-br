---
title: Autenticação e autorização em aplicativos nativos de nuvem
description: Arquitetando aplicativos .NET nativos da nuvem para o Azure | Autenticação e autorização em aplicativos nativos de nuvem
ms.date: 05/13/2020
ms.openlocfilehash: bbd2df110dd7a7dc7363e9c07d87f1fa12f4e464
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161133"
---
# <a name="authentication-and-authorization-in-cloud-native-apps"></a><span data-ttu-id="af760-103">Autenticação e autorização nos aplicativos nativos de nuvem</span><span class="sxs-lookup"><span data-stu-id="af760-103">Authentication and authorization in cloud-native apps</span></span>

<span data-ttu-id="af760-104">A *autenticação* é o processo de determinar a identidade de uma entidade de segurança.</span><span class="sxs-lookup"><span data-stu-id="af760-104">*Authentication* is the process of determining the identity of a security principal.</span></span> <span data-ttu-id="af760-105">A *autorização* é o ato de conceder uma permissão de entidade autenticada para executar uma ação ou acessar um recurso.</span><span class="sxs-lookup"><span data-stu-id="af760-105">*Authorization* is the act of granting an authenticated principal permission to perform an action or access a resource.</span></span> <span data-ttu-id="af760-106">Às vezes, a autenticação é reduzida para `AuthN` e a autorização é reduzida para `AuthZ` .</span><span class="sxs-lookup"><span data-stu-id="af760-106">Sometimes authentication is shortened to `AuthN` and authorization is shortened to `AuthZ`.</span></span> <span data-ttu-id="af760-107">Os aplicativos nativos de nuvem precisam contar com protocolos abertos baseados em HTTP para autenticar entidades de segurança, já que os clientes e aplicativos podem estar em execução em qualquer lugar do mundo em qualquer plataforma ou dispositivo.</span><span class="sxs-lookup"><span data-stu-id="af760-107">Cloud-native applications need to rely on open HTTP-based protocols to authenticate security principals since both clients and applications could be running anywhere in the world on any platform or device.</span></span> <span data-ttu-id="af760-108">O único fator comum é HTTP.</span><span class="sxs-lookup"><span data-stu-id="af760-108">The only common factor is HTTP.</span></span>

<span data-ttu-id="af760-109">Muitas organizações ainda dependem de serviços de autenticação local como o Serviços de Federação do Active Directory (AD FS) (ADFS).</span><span class="sxs-lookup"><span data-stu-id="af760-109">Many organizations still rely on local authentication services like Active Directory Federation Services (ADFS).</span></span> <span data-ttu-id="af760-110">Embora essa abordagem tradicionalmente tenha atendido às organizações para as necessidades de autenticação local, os aplicativos nativos de nuvem se beneficiam de sistemas projetados especificamente para a nuvem.</span><span class="sxs-lookup"><span data-stu-id="af760-110">While this approach has traditionally served organizations well for on premises authentication needs, cloud-native applications benefit from systems designed specifically for the cloud.</span></span> <span data-ttu-id="af760-111">Uma recente consultoria de 2019 do Reino Unido National Cyber Security Centre (NCSC) informa que "as organizações que usam o Azure AD como sua fonte de autenticação primária reduzirão seu risco em comparação com o ADFS".</span><span class="sxs-lookup"><span data-stu-id="af760-111">A recent 2019 United Kingdom National Cyber Security Centre (NCSC) advisory states that "organizations using Azure AD as their primary authentication source will actually lower their risk compared to ADFS."</span></span> <span data-ttu-id="af760-112">Alguns motivos descritos nesta [análise](https://oxfordcomputergroup.com/resources/o365-security-native-cloud-authentication/) incluem:</span><span class="sxs-lookup"><span data-stu-id="af760-112">Some reasons outlined in [this analysis](https://oxfordcomputergroup.com/resources/o365-security-native-cloud-authentication/) include:</span></span>

- <span data-ttu-id="af760-113">Acesso ao conjunto completo de tecnologias de proteção de credenciais da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="af760-113">Access to full set of Microsoft credential protection technologies.</span></span>
- <span data-ttu-id="af760-114">A maioria das organizações já confia no Azure AD até certo ponto.</span><span class="sxs-lookup"><span data-stu-id="af760-114">Most organizations are already relying on Azure AD to some extent.</span></span>
- <span data-ttu-id="af760-115">O hash duplo de hashes NTLM garante que o comprometimento não permitirá credenciais que funcionem no Active Directory local.</span><span class="sxs-lookup"><span data-stu-id="af760-115">Double hashing of NTLM hashes ensures compromise won't allow credentials that work in local Active Directory.</span></span>

## <a name="references"></a><span data-ttu-id="af760-116">Referências</span><span class="sxs-lookup"><span data-stu-id="af760-116">References</span></span>

- [<span data-ttu-id="af760-117">Noções básicas de autenticação</span><span class="sxs-lookup"><span data-stu-id="af760-117">Authentication basics</span></span>](/azure/active-directory/develop/authentication-scenarios)
- [<span data-ttu-id="af760-118">Tokens e declarações de acesso</span><span class="sxs-lookup"><span data-stu-id="af760-118">Access tokens and claims</span></span>](/azure/active-directory/develop/access-tokens)
- [<span data-ttu-id="af760-119">Pode ser hora de eliminar seus serviços de autenticação locais</span><span class="sxs-lookup"><span data-stu-id="af760-119">It may be time to ditch your on premises authentication services</span></span>](https://oxfordcomputergroup.com/resources/o365-security-native-cloud-authentication/)

>[!div class="step-by-step"]
><span data-ttu-id="af760-120">[Anterior](identity.md) 
> [Avançar](azure-active-directory.md)</span><span class="sxs-lookup"><span data-stu-id="af760-120">[Previous](identity.md)
[Next](azure-active-directory.md)</span></span>
