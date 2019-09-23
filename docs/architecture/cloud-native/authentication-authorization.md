---
title: Autenticação e autorização em aplicativos nativos de nuvem
description: Arquitetando aplicativos .NET nativos da nuvem para o Azure | Autenticação e autorização em aplicativos nativos de nuvem
ms.date: 06/30/2019
ms.openlocfilehash: a397175e98c2e8103d2a8c372c81fcca65f19b11
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183724"
---
# <a name="authentication-and-authorization-in-cloud-native-apps"></a>Autenticação e autorização em aplicativos nativos de nuvem

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

A *autenticação* é o processo de determinar a identidade de uma entidade de segurança. A *autorização* é o ato de conceder uma permissão de entidade autenticada para executar uma ação ou acessar um recurso. Às vezes, a autenticação é `AuthN` reduzida para e a autorização é `AuthZ`reduzida para. Os aplicativos nativos de nuvem precisam contar com protocolos abertos baseados em HTTP para autenticar entidades de segurança, já que os clientes e aplicativos podem estar em execução em qualquer lugar do mundo em qualquer plataforma ou dispositivo. O único fator comum é HTTP.

Muitas organizações ainda dependem de serviços de autenticação local como o Serviços de Federação do Active Directory (AD FS) (ADFS). Embora essa abordagem tradicionalmente tenha atendido às organizações para as necessidades de autenticação local, os aplicativos nativos de nuvem se beneficiam de sistemas projetados especificamente para a nuvem. Uma recente consultoria de 2019 do Reino Unido National Cyber Security Centre (NCSC) informa que "as organizações que usam o Azure AD como sua fonte de autenticação primária reduzirão seu risco em comparação com o ADFS". Alguns motivos descritos nesta [análise](https://oxfordcomputergroup.com/resources/o365-security-native-cloud-authentication/) incluem:

- Acesso ao conjunto completo de tecnologias de proteção de credenciais da Microsoft.
- A maioria das organizações já confia no Azure AD até certo ponto.
- O hash duplo de hashes NTLM garante que o comprometimento não permitirá credenciais que funcionem no Active Directory local.

## <a name="references"></a>Referências

- [Noções básicas de autenticação](https://docs.microsoft.com/azure/active-directory/develop/authentication-scenarios)
- [Tokens e declarações de acesso](https://docs.microsoft.com/azure/active-directory/develop/access-tokens)
- [Pode ser hora de eliminar seus serviços de autenticação locais](https://oxfordcomputergroup.com/resources/o365-security-native-cloud-authentication/)

>[!div class="step-by-step"]
>[Anterior](identity.md)
>[Próximo](azure-active-directory.md)
