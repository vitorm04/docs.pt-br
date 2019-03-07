---
title: 1004 - WorkflowInstanceAborted
ms.date: 03/30/2017
ms.assetid: edb9ab8c-0b9a-488d-aa96-9c8c7984b53c
ms.openlocfilehash: d34f6f1ab6af8e06a0f28fb043faf9fe16a8b211
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485181"
---
# <a name="1004---workflowinstanceaborted"></a>1004 - WorkflowInstanceAborted

## <a name="properties"></a>Propriedades

|||
|-|-|
|ID|1004|
|Palavras-chave|WFRuntime|
|Nível|Informações|
|Canal|Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração|

## <a name="description"></a>Descrição

Indica que uma instância de fluxo de trabalho foi anulado com uma exceção.

## <a name="message"></a>Mensagem

Identificação de WorkflowInstance: “%1 " foi anuladas com uma exceção.

## <a name="details"></a>Detalhes

|Nome do item de dados|Tipo de item de dados|Descrição|
|--------------------|--------------------|-----------------|
|WorkflowInstanceId|`xs:string`|A identificação de instância para o fluxo de trabalho|
|Exceção|`xs:string`|Os detalhes de exceção para a exceção|
|AppDomain|`xs:string`|A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.|
