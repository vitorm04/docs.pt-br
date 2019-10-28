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
# <a name="operating-system-resources-required-by-wcf"></a><span data-ttu-id="00905-102">Recursos do sistema operacional exigidos pelo WCF</span><span class="sxs-lookup"><span data-stu-id="00905-102">Operating System Resources Required by WCF</span></span>

<span data-ttu-id="00905-103">O Windows Communication Foundation (WCF) depende de vários recursos que são fornecidos pelo sistema operacional para funcionar.</span><span class="sxs-lookup"><span data-stu-id="00905-103">Windows Communication Foundation (WCF) depends on several resources that are provided by the operating system to function.</span></span> <span data-ttu-id="00905-104">A tabela a seguir lista esses recursos:</span><span class="sxs-lookup"><span data-stu-id="00905-104">The following table lists those resources:</span></span>

|<span data-ttu-id="00905-105">Recurso</span><span class="sxs-lookup"><span data-stu-id="00905-105">Resource</span></span>|<span data-ttu-id="00905-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="00905-106">Description</span></span>|
|--------------|-----------------|
|<span data-ttu-id="00905-107">Coordenador de Transações Distribuídas da Microsoft (MSDTC)</span><span class="sxs-lookup"><span data-stu-id="00905-107">Microsoft Distributed Transaction Coordinator (MSDTC)</span></span>|<span data-ttu-id="00905-108">Necessário para dar suporte a transações OleTx.</span><span class="sxs-lookup"><span data-stu-id="00905-108">Required to support OleTx transactions.</span></span>|
|<span data-ttu-id="00905-109">Serviços de Informações da Internet (IIS)</span><span class="sxs-lookup"><span data-stu-id="00905-109">Internet Information Services (IIS)</span></span>|<span data-ttu-id="00905-110">Obrigatório se você quiser usar o IIS para hospedar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="00905-110">Required if you want to use IIS to host your application.</span></span>|
|<span data-ttu-id="00905-111">Serviço de Ativação de Processos do Windows (WAS)</span><span class="sxs-lookup"><span data-stu-id="00905-111">Windows Process Activation Service (WAS)</span></span>|<span data-ttu-id="00905-112">Obrigatório se você quiser usar o WAS para hospedar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="00905-112">Required if you want to use WAS to host your application.</span></span>|
