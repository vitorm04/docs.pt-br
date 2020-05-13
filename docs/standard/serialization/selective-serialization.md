---
title: Serialização seletiva
description: Este artigo mostra como marcar campos com o atributo NonSerialized, que impede que esse campo seja serializado.
ms.date: 08/07/2017
dev_langs:
- CSharp
helpviewer_keywords:
- serialization, selective serialization
- binary serialization, selective serialization
ms.assetid: 39c56635-95d2-4afd-aff1-b022e7649bb3
ms.openlocfilehash: c7203c4ea13c65f8d88c55de96988d3b1d9e9611
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379171"
---
# <a name="selective-serialization"></a><span data-ttu-id="3de2b-103">Serialização seletiva</span><span class="sxs-lookup"><span data-stu-id="3de2b-103">Selective serialization</span></span>
<span data-ttu-id="3de2b-104">Uma classe geralmente contém os campos que não devem ser serializados.</span><span class="sxs-lookup"><span data-stu-id="3de2b-104">A class often contains fields that shouldn't be serialized.</span></span> <span data-ttu-id="3de2b-105">Por exemplo, presuma que uma classe armazene uma ID de thread em uma variável de membro.</span><span class="sxs-lookup"><span data-stu-id="3de2b-105">For example, assume a class stores a thread ID in a member variable.</span></span> <span data-ttu-id="3de2b-106">Quando a classe é desserializada, o thread que armazenou a ID de quando a classe foi serializada pode não estar mais em execução; portanto, serializar esse valor não faz sentido.</span><span class="sxs-lookup"><span data-stu-id="3de2b-106">When the class is deserialized, the thread stored the ID for when the class was serialized might no longer be running; so serializing this value doesn't make sense.</span></span> <span data-ttu-id="3de2b-107">Você pode impedir que variáveis de membros sejam serializadas marcando-as com o atributo [NonSerialized](xref:System.NonSerializedAttribute) da maneira a seguir.</span><span class="sxs-lookup"><span data-stu-id="3de2b-107">You can prevent member variables from being serialized by marking them with the [NonSerialized](xref:System.NonSerializedAttribute) attribute as follows.</span></span>  
  
```csharp  
[Serializable]  
public class MyObject
{  
  public int n1;  
  [NonSerialized] public int n2;  
  public String str;  
}  
```

<span data-ttu-id="3de2b-108">Se possível, crie um objeto que possa conter dados confidenciais de segurança não serializáveis.</span><span class="sxs-lookup"><span data-stu-id="3de2b-108">If possible, make an object that could contain security-sensitive data nonserializable.</span></span> <span data-ttu-id="3de2b-109">Se o objeto tiver que ser serializado, aplique o atributo `NonSerialized` em campos específicos que armazenam dados confidenciais.</span><span class="sxs-lookup"><span data-stu-id="3de2b-109">If the object must be serialized, apply the `NonSerialized` attribute to specific fields that store sensitive data.</span></span> <span data-ttu-id="3de2b-110">Se você não excluir esses campos da serialização, esteja ciente de que os dados que eles armazenam serão expostos em qualquer código que tenha permissão para serializar.</span><span class="sxs-lookup"><span data-stu-id="3de2b-110">If you don't exclude these fields from serialization, be aware that the data they store are exposed to any code that has permission to serialize.</span></span> <span data-ttu-id="3de2b-111">Para obter mais informações sobre como escrever um código de serialização segura, consulte [Segurança e serialização](../../../docs/framework/misc/security-and-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="3de2b-111">For more information about writing secure serialization code, see [Security and Serialization](../../../docs/framework/misc/security-and-serialization.md).</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
## <a name="see-also"></a><span data-ttu-id="3de2b-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="3de2b-112">See also</span></span>

- [<span data-ttu-id="3de2b-113">Serialização binária</span><span class="sxs-lookup"><span data-stu-id="3de2b-113">Binary Serialization</span></span>](binary-serialization.md)
- [<span data-ttu-id="3de2b-114">Serialização de XML e SOAP</span><span class="sxs-lookup"><span data-stu-id="3de2b-114">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)
- [<span data-ttu-id="3de2b-115">Segurança e serialização</span><span class="sxs-lookup"><span data-stu-id="3de2b-115">Security and Serialization</span></span>](../../../docs/framework/misc/security-and-serialization.md)
