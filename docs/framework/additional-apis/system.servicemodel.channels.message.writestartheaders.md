---
title: Método Message. WriteStartHeaders (System. ServiceModel. Channels)
ms.date: 11/01/2019
topic_type:
- apiref
api_name:
- System.ServiceModel.Channels.Message.WriteStartHeaders
api_location:
- system.servicemodel.dll
api_type:
- Assembly
ms.openlocfilehash: c826e6a3b976e5705e9815586441e8a25b64f76e
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77214871"
---
# <a name="messagewritestartheaders-method"></a><span data-ttu-id="a96cd-102">Método Message. WriteStartHeaders</span><span class="sxs-lookup"><span data-stu-id="a96cd-102">Message.WriteStartHeaders Method</span></span>

<span data-ttu-id="a96cd-103">Grava o cabeçalho inicial em um arquivo XML chamando o método <xref:System.ServiceModel.Channels.Message.OnWriteStartHeaders%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a96cd-103">Writes the start header into an XML file by calling the <xref:System.ServiceModel.Channels.Message.OnWriteStartHeaders%2A?displayProperty=nameWithType> method.</span></span>

```csharp
internal void WriteStartHeaders(XmlDictionaryWriter writer)
```

## <a name="parameters"></a><span data-ttu-id="a96cd-104">parâmetros</span><span class="sxs-lookup"><span data-stu-id="a96cd-104">Parameters</span></span>

- <span data-ttu-id="a96cd-105">`writer` <xref:System.Xml.XmlDictionaryWriter></span><span class="sxs-lookup"><span data-stu-id="a96cd-105">`writer` <xref:System.Xml.XmlDictionaryWriter></span></span>\
  <span data-ttu-id="a96cd-106">O gravador usado para gravar o cabeçalho inicial em um arquivo XML.</span><span class="sxs-lookup"><span data-stu-id="a96cd-106">The writer that is used to write the start header into an XML file.</span></span>

## <a name="remarks"></a><span data-ttu-id="a96cd-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="a96cd-107">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="a96cd-108">O método `Message.WriteStartHeaders` é interno e não deve ser usado diretamente no seu código.</span><span class="sxs-lookup"><span data-stu-id="a96cd-108">The `Message.WriteStartHeaders` method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="a96cd-109">A Microsoft não oferece suporte ao uso desse método em um aplicativo de produção em qualquer circunstância.</span><span class="sxs-lookup"><span data-stu-id="a96cd-109">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="a96cd-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a96cd-110">Requirements</span></span>

<span data-ttu-id="a96cd-111">**Namespace:** <xref:System.ServiceModel.Channels></span><span class="sxs-lookup"><span data-stu-id="a96cd-111">**Namespace:** <xref:System.ServiceModel.Channels></span></span>

<span data-ttu-id="a96cd-112">**Assembly:** System. ServiceModel. dll</span><span class="sxs-lookup"><span data-stu-id="a96cd-112">**Assembly:** System.ServiceModel.dll</span></span>

<span data-ttu-id="a96cd-113">**.NET Framework versões:** Disponível desde 3,0.</span><span class="sxs-lookup"><span data-stu-id="a96cd-113">**.NET Framework versions:** Available since 3.0.</span></span>
