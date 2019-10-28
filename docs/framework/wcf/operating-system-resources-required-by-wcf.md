---
title: Recursos do sistema operacional exigidos pelo WCF
ms.date: 03/30/2017
ms.assetid: cdd9a331-53fe-4e0d-bdfe-782264aec5c9
ms.openlocfilehash: c2c26d769424a8d0655591cb10b4b13df8a15884
ms.sourcegitcommit: 9b2ef64c4fc10a4a10f28a223d60d17d7d249ee8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/26/2019
ms.locfileid: "72961144"
---
# <a name="operating-system-resources-required-by-wcf"></a>Recursos do sistema operacional exigidos pelo WCF

O Windows Communication Foundation (WCF) depende de vários recursos que são fornecidos pelo sistema operacional para funcionar. A tabela a seguir lista esses recursos:

|Recurso|Descrição|
|--------------|-----------------|
|Coordenador de Transações Distribuídas da Microsoft (MSDTC)|Necessário para dar suporte a transações OleTx.|
|Serviços de Informações da Internet (IIS)|Obrigatório se você quiser usar o IIS para hospedar seu aplicativo.|
|Serviço de Ativação de Processos do Windows (WAS)|Obrigatório se você quiser usar o WAS para hospedar seu aplicativo.|
