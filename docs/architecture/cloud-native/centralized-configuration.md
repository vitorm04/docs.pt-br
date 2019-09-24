---
title: Configuração centralizada
description: A configuração centralizada usando o Azure Key Vault pode facilitar o gerenciamento de aplicativos nativos de nuvem.
ms.date: 06/30/2019
ms.openlocfilehash: 4c516b6773d913acd71ff06742302e9766a141e2
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71214002"
---
# <a name="centralized-configuration"></a>Configuração centralizada

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Os aplicativos nativos de nuvem envolvem muitos outros serviços em execução do que os aplicativos monolíticos de instância única tradicionais. O gerenciamento de definições de configuração para dezenas de serviços interdependentes pode ser desafiador, motivo pelo qual os repositórios de configuração centralizados geralmente são implementados para aplicativos distribuídos.

Conforme discutido no [capítulo 1](introduction.md), as recomendações do aplicativo de doze fatores exigem uma separação estrita entre o código e a configuração. Isso significa que o armazenamento de definições de configuração como constantes ou valores literais no código é uma violação. Essa recomendação existe porque o mesmo código deve ser usado em vários ambientes, incluindo desenvolvimento, teste, preparo e produção. No entanto, é provável que os valores de configuração variem entre cada um desses ambientes. Portanto, os valores de configuração devem ser armazenados no próprio ambiente ou o ambiente deve armazenar as credenciais em um repositório de configurações centralizado.

O aplicativo eShopOnContainers inclui arquivos de configurações de aplicativo local com cada microserviço. Esses arquivos são verificados no controle do código-fonte, mas não incluem segredos de produção, como cadeias de conexão ou chaves de API. Em produção, as configurações individuais podem ser substituídas por variáveis de ambiente por serviço. Essa é uma prática comum para aplicativos hospedados, mas não fornece um repositório de configuração central. Para dar suporte ao gerenciamento centralizado de definições de configuração, cada microserviço inclui uma configuração para alternar entre o uso de configurações locais ou configurações de Azure Key Vault.

## <a name="azure-key-vault"></a>Azure Key Vault

Azure Key Vault fornece armazenamento seguro de tokens, senhas, certificados, chaves de API e outros segredos confidenciais. O acesso a Key Vault requer autenticação e autorização apropriadas do chamador, que no caso dos microserviços eShopOnContainers significam o uso de uma combinação ClientId/ClientSecret. Não faça check-in dessas credenciais no controle do código-fonte, mas, em vez disso, defina no ambiente do aplicativo. O acesso direto a Key Vault do AKS pode ser obtido usando [Key Vault FlexVolume](https://github.com/Azure/kubernetes-keyvault-flexvol).

Com a configuração centralizada, as configurações que se aplicam ao aplicativo inteiro, como o ponto de extremidade de registro em log centralizado, podem ser definidas uma vez e usadas por cada parte do aplicativo distribuído. Embora os microserviços devam ser independentes um do outro, normalmente ainda serão algumas dependências compartilhadas cujos detalhes de configuração podem se beneficiar de um repositório de configuração centralizado.

>[!div class="step-by-step"]
>[Anterior](deploy-eshoponcontainers-azure.md)
>[Próximo](scale-applications.md)
