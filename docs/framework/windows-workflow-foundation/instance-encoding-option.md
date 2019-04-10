---
title: Padrão de codificação de instância
ms.date: 03/30/2017
ms.assetid: 89e4b029-4f68-438c-8117-9b21fe094ef4
ms.openlocfilehash: c4de7c45d899f45a7b5b71d563257d9accb8fdbb
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59315615"
---
# <a name="instance-encoding-option"></a>Padrão de codificação de instância
O **a opção de codificação de instância** propriedade de Store de instância de fluxo de trabalho do SQL permite que você especifique se o provedor de persistência do SQL deve compactar as informações de estado da instância de fluxo de trabalho usando o algoritmo de GZip antes de salvar o informações no banco de dados de persistência. Os valores permitidos para essa propriedade são: GZip e None. O valor padrão é None. A lista a seguir descreve as opções.  
  
1. **GZip**. O provedor de persistência codificação informações de estado usando o algoritmo de GZip antes de manter informações de estado na base de dados de persistência.  
  
2. **Nenhum**. O provedor de persistência não codificação informações de estado antes de salvar informações na base de dados de persistência.  
  
 Informações de estado da instância de fluxo de trabalho de codificação que usa o GZip reduz o consumo de memória na base de dados SQL e também reduz o consumo de rede se o base de dados reside em um outro computador na rede do computador no qual o host serviço de fluxo de trabalho está sendo executado. Uma orientação geral é definir a **a opção de codificação de instância** propriedade **None** se o estado da instância de fluxo de trabalho for pequeno.
