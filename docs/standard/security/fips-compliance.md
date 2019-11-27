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
# <a name="net-core-federal-information-processing-standard-fips-compliance"></a>Conformidade do padrão FIPS do .NET Core (FIPS)

A publicação 140-2 do padrão FIPS (FIPS) é um padrão do governo dos EUA que define os requisitos mínimos de segurança para módulos de criptografia em produtos de tecnologia da informação, conforme definido na seção 5131 das informações Lei de reforma do gerenciamento de tecnologia de 1996.

.NET Core:

* Passa chamadas de primitivos criptográficos para os módulos padrão fornecidos pelo sistema operacional subjacente.
* **Não** impõe o uso de algoritmos ou tamanhos de chave FIPS aprovados em aplicativos .NET Core.

O administrador do sistema é responsável por configurar a conformidade com FIPS para um sistema operacional.

Se o código for escrito para um ambiente compatível com FIPS, o desenvolvedor será responsável por garantir que os algoritmos FIPS não compatíveis não sejam usados.

Para obter mais informações sobre a conformidade com FIPS, consulte os seguintes artigos:

* [Conformidade com o Windows FIPS](/windows/security/threat-protection/fips-140-validation)
* [Configurando o Windows para conformidade com FIPS](/windows/security/threat-protection/security-policy-settings/system-cryptography-use-fips-compliant-algorithms-for-encryption-hashing-and-signing)
* [10,2. PADRÃO DE PROCESSAMENTO DE INFORMAÇÕES FEDERAIS (FIPS)](https://access.redhat.com/documentation/red_hat_enterprise_linux/6/html/security_guide/sect-security_guide-federal_standards_and_regulations-federal_information_processing_standard)
