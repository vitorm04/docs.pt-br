---
title: Conformidade com FIPS-.NET Core
description: Explica a conformidade do .NET Core padrão FIPS (FIPS).
ms.date: 11/20/2019
author: Rick-Anderson
ms.author: riande
ms.openlocfilehash: cf640c857e79ae811dd38d57a0e5301b7bc96572
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74205062"
---
# <a name="net-core-federal-information-processing-standard-fips-compliance"></a><span data-ttu-id="dcb58-103">Conformidade do padrão FIPS do .NET Core (FIPS)</span><span class="sxs-lookup"><span data-stu-id="dcb58-103">.NET Core Federal Information Processing Standard (FIPS) compliance</span></span>

<span data-ttu-id="dcb58-104">A publicação 140-2 do padrão FIPS (FIPS) é um padrão do governo dos EUA que define os requisitos mínimos de segurança para módulos de criptografia em produtos de tecnologia da informação, conforme definido na seção 5131 das informações Lei de reforma do gerenciamento de tecnologia de 1996.</span><span class="sxs-lookup"><span data-stu-id="dcb58-104">The Federal Information Processing Standard (FIPS) Publication 140-2 is a U.S. government standard that defines minimum security requirements for cryptographic modules in information technology products, as defined in Section 5131 of the Information Technology Management Reform Act of 1996.</span></span>

<span data-ttu-id="dcb58-105">.NET Core:</span><span class="sxs-lookup"><span data-stu-id="dcb58-105">.NET Core:</span></span>

* <span data-ttu-id="dcb58-106">Passa chamadas de primitivos criptográficos para os módulos padrão fornecidos pelo sistema operacional subjacente.</span><span class="sxs-lookup"><span data-stu-id="dcb58-106">Passes cryptographic primitives calls through to the standard modules the underlying operating system provides.</span></span>
* <span data-ttu-id="dcb58-107">**Não** impõe o uso de algoritmos ou tamanhos de chave FIPS aprovados em aplicativos .NET Core.</span><span class="sxs-lookup"><span data-stu-id="dcb58-107">Does **not** enforce the use of FIPS Approved algorithms or key sizes in .NET Core apps.</span></span>

<span data-ttu-id="dcb58-108">O administrador do sistema é responsável por configurar a conformidade com FIPS para um sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="dcb58-108">The system administrator is responsible for configuring the FIPS compliance for an operating system.</span></span>

<span data-ttu-id="dcb58-109">Se o código for escrito para um ambiente compatível com FIPS, o desenvolvedor será responsável por garantir que os algoritmos FIPS não compatíveis não sejam usados.</span><span class="sxs-lookup"><span data-stu-id="dcb58-109">If code is written for a FIPS-compliant environment, the developer is responsible for ensuring that non-compliant FIPS algorithms aren't used.</span></span>

<span data-ttu-id="dcb58-110">Para obter mais informações sobre a conformidade com FIPS, consulte os seguintes artigos:</span><span class="sxs-lookup"><span data-stu-id="dcb58-110">For more information on FIPS compliance, see the following articles:</span></span>

* [<span data-ttu-id="dcb58-111">Conformidade com o Windows FIPS</span><span class="sxs-lookup"><span data-stu-id="dcb58-111">Windows FIPS Compliance</span></span>](/windows/security/threat-protection/fips-140-validation)
* [<span data-ttu-id="dcb58-112">Configurando o Windows para conformidade com FIPS</span><span class="sxs-lookup"><span data-stu-id="dcb58-112">Configuring Windows for FIPS Compliance</span></span>](/windows/security/threat-protection/security-policy-settings/system-cryptography-use-fips-compliant-algorithms-for-encryption-hashing-and-signing)
* [<span data-ttu-id="dcb58-113">10,2. PADRÃO DE PROCESSAMENTO DE INFORMAÇÕES FEDERAIS (FIPS)</span><span class="sxs-lookup"><span data-stu-id="dcb58-113">10.2. FEDERAL INFORMATION PROCESSING STANDARD (FIPS)</span></span>](https://access.redhat.com/documentation/red_hat_enterprise_linux/6/html/security_guide/sect-security_guide-federal_standards_and_regulations-federal_information_processing_standard)
