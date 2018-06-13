---
title: Padrão de codificação de instância
ms.date: 03/30/2017
ms.assetid: 89e4b029-4f68-438c-8117-9b21fe094ef4
ms.openlocfilehash: cfe45428f546b6f47709c321099efdf7fbb25ef4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33512532"
---
# <a name="instance-encoding-option"></a>Padrão de codificação de instância
O **a opção de codificação de instância** propriedade do repositório de instância de fluxo de trabalho de SQL permite que você especifique se o provedor de persistência do SQL deve compactar as informações de estado da instância de fluxo de trabalho usando o algoritmo GZip antes de salvar o informações no banco de dados de persistência. Os valores permitidos para essa propriedade são: GZip e quaisquer. O valor padrão é None. A lista a seguir descreve as opções.  
  
1.  **GZip**. O provedor de persistência codificação informações de estado usando o algoritmo de GZip antes de manter informações de estado na base de dados de persistência.  
  
2.  **Nenhum**. O provedor de persistência não codificação informações de estado antes de salvar informações na base de dados de persistência.  
  
 Informações de estado da instância de fluxo de trabalho de codificação que usa o GZip reduz o consumo de memória na base de dados SQL e também reduz o consumo de rede se o base de dados reside em um outro computador na rede do computador no qual o host serviço de fluxo de trabalho está sendo executado. Uma orientação geral é definir o **a opção de codificação de instância** propriedade **nenhum** se o estado da instância de fluxo de trabalho for pequeno.
