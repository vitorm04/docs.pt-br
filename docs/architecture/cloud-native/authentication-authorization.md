---
title: Autenticação e Autorização em aplicativos nativos da nuvem
description: Arquitetando aplicativos nativos da nuvem .NET para Azure | Autenticação e Autorização em Aplicativos Nativos da Nuvem
ms.date: 03/02/2020
ms.openlocfilehash: 6261a0a72405bc1c984a04a7851aea4dd6664ddf
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805550"
---
# <a name="authentication-and-authorization-in-cloud-native-apps"></a>Autenticação e autorização nos aplicativos nativos de nuvem

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

*Autenticação* é o processo de determinar a identidade de um diretor de segurança. *Autorização* é o ato de conceder uma permissão principal autenticada para realizar uma ação ou acessar um recurso. Às vezes, a `AuthN` autenticação é encurtada e a autorização é encurtada para `AuthZ`. Os aplicativos nativos da nuvem precisam contar com protocolos abertos baseados em HTTP para autenticar os princípios de segurança, já que tanto clientes quanto aplicativos podem estar sendo executados em qualquer lugar do mundo em qualquer plataforma ou dispositivo. O único fator comum é http.

Muitas organizações ainda dependem de serviços locais de autenticação, como o Active Directory Federation Services (ADFS). Embora essa abordagem tenha tradicionalmente servido bem às organizações para necessidades de autenticação no local, aplicativos nativos da nuvem se beneficiam de sistemas projetados especificamente para a nuvem. Um recente aviso do Centro Nacional de Segurança Cibernética do Reino Unido (NCSC) de 2019 afirma que "as organizações que usam o Azure AD como sua principal fonte de autenticação reduzirão seu risco em comparação com as ADFS". Algumas razões descritas [nesta análise](https://oxfordcomputergroup.com/resources/o365-security-native-cloud-authentication/) incluem:

- Acesso ao conjunto completo de tecnologias de proteção de credenciais da Microsoft.
- A maioria das organizações já está confiando no Azure AD até certo ponto.
- O hashing duplo dos hashes NTLM garante que o compromisso não permitirá credenciais que funcionem no Active Directory local.

## <a name="references"></a>Referências

- [Noções básicas de autenticação](https://docs.microsoft.com/azure/active-directory/develop/authentication-scenarios)
- [Tokens de acesso e reclamações](https://docs.microsoft.com/azure/active-directory/develop/access-tokens)
- [Talvez seja hora de abandonar seus serviços de autenticação no local](https://oxfordcomputergroup.com/resources/o365-security-native-cloud-authentication/)

>[!div class="step-by-step"]
>[Próximo](identity.md)
>[anterior](azure-active-directory.md)
