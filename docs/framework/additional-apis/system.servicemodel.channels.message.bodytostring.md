---
title: Método Message. BodyToString (System. ServiceModel. Channels)
ms.date: 11/01/2019
topic_type:
- apiref
api_name:
- System.ServiceModel.Channels.Message.BodyToString
api_location:
- system.servicemodel.dll
api_type:
- Assembly
ms.openlocfilehash: 9f1f852c0bd82299fd40afe66a5f90cd7c0335cf
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215502"
---
# <a name="messagebodytostring-method"></a><span data-ttu-id="83b42-102">Método Message. BodyToString</span><span class="sxs-lookup"><span data-stu-id="83b42-102">Message.BodyToString Method</span></span>

<span data-ttu-id="83b42-103">Converte o corpo da mensagem em uma cadeia de caracteres chamando o método <xref:System.ServiceModel.Channels.Message.OnBodyToString%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="83b42-103">Converts the message body into a string by calling the <xref:System.ServiceModel.Channels.Message.OnBodyToString%2A?displayProperty=nameWithType> method.</span></span>

```csharp
internal void BodyToString(XmlDictionaryWriter writer);
```

## <a name="parameters"></a><span data-ttu-id="83b42-104">parâmetros</span><span class="sxs-lookup"><span data-stu-id="83b42-104">Parameters</span></span>

- <span data-ttu-id="83b42-105">`writer` <xref:System.Xml.XmlDictionaryWriter></span><span class="sxs-lookup"><span data-stu-id="83b42-105">`writer` <xref:System.Xml.XmlDictionaryWriter></span></span>\
  <span data-ttu-id="83b42-106">O gravador usado para converter o corpo da mensagem em uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="83b42-106">The writer that is used to convert the message body to a string.</span></span>

## <a name="remarks"></a><span data-ttu-id="83b42-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="83b42-107">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="83b42-108">O método `Message.BodyToString` é interno e não deve ser usado diretamente no seu código.</span><span class="sxs-lookup"><span data-stu-id="83b42-108">The `Message.BodyToString` method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="83b42-109">A Microsoft não oferece suporte ao uso desse método em um aplicativo de produção em qualquer circunstância.</span><span class="sxs-lookup"><span data-stu-id="83b42-109">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="83b42-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="83b42-110">Requirements</span></span>

<span data-ttu-id="83b42-111">**Namespace:** <xref:System.ServiceModel.Channels></span><span class="sxs-lookup"><span data-stu-id="83b42-111">**Namespace:** <xref:System.ServiceModel.Channels></span></span>

<span data-ttu-id="83b42-112">**Assembly:** System. ServiceModel. dll</span><span class="sxs-lookup"><span data-stu-id="83b42-112">**Assembly:** System.ServiceModel.dll</span></span>

<span data-ttu-id="83b42-113">**.NET Framework versões:** Disponível desde 3,0.</span><span class="sxs-lookup"><span data-stu-id="83b42-113">**.NET Framework versions:** Available since 3.0.</span></span>
