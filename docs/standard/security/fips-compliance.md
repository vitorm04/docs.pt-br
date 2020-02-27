---
title: Conformidade com FIPS-.NET Core
description: Explica a conformidade do .NET Core padrão FIPS (FIPS).
ms.date: 11/20/2019
author: Rick-Anderson
ms.author: riande
ms.openlocfilehash: 84d6edc6975af0484bb67999ad5891eaf4db057d
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626952"
---
# <a name="net-core-federal-information-processing-standard-fips-compliance"></a><span data-ttu-id="fe331-103">Conformidade do padrão FIPS do .NET Core (FIPS)</span><span class="sxs-lookup"><span data-stu-id="fe331-103">.NET Core Federal Information Processing Standard (FIPS) compliance</span></span>

<span data-ttu-id="fe331-104">A publicação 140-2 do padrão FIPS (FIPS) é um padrão do governo dos EUA que define os requisitos mínimos de segurança para módulos de criptografia em produtos de tecnologia da informação, conforme definido na seção 5131 das informações Lei de reforma do gerenciamento de tecnologia de 1996.</span><span class="sxs-lookup"><span data-stu-id="fe331-104">The Federal Information Processing Standard (FIPS) Publication 140-2 is a U.S. government standard that defines minimum security requirements for cryptographic modules in information technology products, as defined in Section 5131 of the Information Technology Management Reform Act of 1996.</span></span>

<span data-ttu-id="fe331-105">.NET Core:</span><span class="sxs-lookup"><span data-stu-id="fe331-105">.NET Core:</span></span>

* <span data-ttu-id="fe331-106">Passa chamadas de primitivos criptográficos para os módulos padrão fornecidos pelo sistema operacional subjacente.</span><span class="sxs-lookup"><span data-stu-id="fe331-106">Passes cryptographic primitives calls through to the standard modules the underlying operating system provides.</span></span>
* <span data-ttu-id="fe331-107">**Não** impõe o uso de algoritmos ou tamanhos de chave FIPS aprovados em aplicativos .NET Core.</span><span class="sxs-lookup"><span data-stu-id="fe331-107">Does **not** enforce the use of FIPS Approved algorithms or key sizes in .NET Core apps.</span></span>

<span data-ttu-id="fe331-108">O administrador do sistema é responsável por configurar a conformidade com FIPS para um sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="fe331-108">The system administrator is responsible for configuring the FIPS compliance for an operating system.</span></span>

<span data-ttu-id="fe331-109">Se o código for escrito para um ambiente compatível com FIPS, o desenvolvedor será responsável por garantir que os algoritmos FIPS não compatíveis não sejam usados.</span><span class="sxs-lookup"><span data-stu-id="fe331-109">If code is written for a FIPS-compliant environment, the developer is responsible for ensuring that non-compliant FIPS algorithms aren't used.</span></span>

<span data-ttu-id="fe331-110">Para obter mais informações sobre a conformidade com FIPS, consulte os seguintes artigos:</span><span class="sxs-lookup"><span data-stu-id="fe331-110">For more information on FIPS compliance, see the following articles:</span></span>

* [<span data-ttu-id="fe331-111">Conformidade com o Windows FIPS</span><span class="sxs-lookup"><span data-stu-id="fe331-111">Windows FIPS Compliance</span></span>](/windows/security/threat-protection/fips-140-validation)
* [<span data-ttu-id="fe331-112">Configurando o Windows para conformidade com FIPS</span><span class="sxs-lookup"><span data-stu-id="fe331-112">Configuring Windows for FIPS Compliance</span></span>](/windows/security/threat-protection/security-policy-settings/system-cryptography-use-fips-compliant-algorithms-for-encryption-hashing-and-signing)
* [<span data-ttu-id="fe331-113">Capítulo 8. Normas e padrões federais Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="fe331-113">Chapter 8. Federal Standards and Regulations Red Hat Enterprise Linux 7</span></span>](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/security_guide/chap-federal_standards_and_regulations)
