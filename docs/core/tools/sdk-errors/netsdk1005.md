---
title: 'NETSDK1005 e NETSDK1047: o arquivo de ativo está com destino ausente'
description: Como resolver o problema de um arquivo de ativo que não tem um destino.
author: sfoslund
ms.topic: error-reference
ms.date: 10/09/2020
f1_keywords:
- NETSDK1005
- NETSDK1047
ms.openlocfilehash: 6c22fd8c79c2ac6e024b46b4f67e08011d42efc6
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2020
ms.locfileid: "91957134"
---
# <a name="netsdk1005-and-netsdk1047-asset-file-is-missing-target"></a>NETSDK1005 e NETSDK1047: o arquivo de ativo está com destino ausente

**Este artigo aplica-se a:** ✔️ o SDK do .NET 2.1.100 e versões posteriores

Quando o SDK do .NET emite o erro NETSDK1005 ou NETSDK1047, o arquivo de ativos do projeto não tem informações sobre uma de suas estruturas de destino. Normalmente, isso pode ser corrigido garantindo que a restauração seja executada e que o valor de destino ausente seja incluído na `TargetFrameworks` Propriedade do seu projeto.

> [!NOTE]
> Houve um problema conhecido com as primeiras compilações do .NET 5 Preview 8 quando usadas com versões do Visual Studio 16,8 visualizações que resultaram nesse erro. Especificamente, se o destino ausente for `net5.0-windows7.0` ou `net5.0` , verifique se você atualizou para as versões mais recentes do Visual Studio e do SDK do .NET 5.
