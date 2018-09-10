---
title: Gerenciar as instalações do .NET Core
description: Gerencie várias versões do SDK do .NET Core e do Tempo de Execução em seu computador, trabalhando com as estratégias de instalação lado a lado.
author: leecow
ms.author: wiwagn
ms.date: 08/22/2018
ms.openlocfilehash: 06c3f43e7917efb8fd31898044d8f5d920c2cada
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43485446"
---
# <a name="manage-net-core-installations"></a>Gerenciar as instalações do .NET Core

O .NET core permite que várias versões do SDK e do Tempo de Execução existam lado a lado, permitindo a flexibilidade de dependência da versão para compilação e execução de aplicativos do .NET Core. Esses comportamentos de roll forward de versão automática e instalação oferecem benefícios valiosos, mas uma grande desvantagem. À medida que as atualizações do SDK do .NET Core ou do Tempo de Execução do .NET Core são instaladas, as versões anteriores permanecem no disco. Várias versões instaladas aumentam o uso de disco ao longo do tempo. Mais de 50 atualizações do SDK do .NET Core foram lançadas. Pode haver muitas versões do SDK e do Tempo de Execução instaladas no seu sistema que podem ser removidas.

## <a name="safe-to-remove"></a>É seguro remover?

Os comportamentos de [seleção de versão do .NET Core](selection.md) e a compatibilidade do tempo de execução do .NET Core com as atualizações permitem a remoção segura de versões anteriores. As atualizações de tempo de execução do .NET core são compatíveis com uma “banda” de versão principal como 1.x e 2.x. Além disso, versões mais recentes do SDK do .NET Core geralmente mantêm a capacidade de compilar aplicativos destinados a versões anteriores do tempo de execução de uma maneira compatível.

Em geral, você precisa apenas do SDK mais recente e da versão de patch mais recente dos tempos de execução necessários para seu aplicativo. Instâncias nas quais reter versões mais antigas do SDK ou do Tempo de Execução incluem a manutenção de aplicativos baseados em project.json.  A menos que seu aplicativo tenha motivos específicos para tempos de execução ou SDKs anteriores, você pode remover com segurança as versões mais antigas.

Os métodos para remover o .NET Core variam de uma plataforma para outra e mudam um pouco entre as versões do .NET Core. Para obter detalhes sobre como remover versões do .NET Core que não são mais necessárias, consulte [“Como remover o SDK e o Tempo de Execução do .Net Core”](remove-runtime-sdk-versions.md) na [documentação do .NET Core](../index.md).
