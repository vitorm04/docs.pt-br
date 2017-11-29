---
title: "Serialização seletiva"
ms.date: 08/07/2017
ms.prod: .net
ms.topic: article
dev_langs: CSharp
helpviewer_keywords:
- serialization, selective serialization
- binary serialization, selective serialization
ms.assetid: 39c56635-95d2-4afd-aff1-b022e7649bb3
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f583c0c7f2895b16ac0aea883dd98b4768179127
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="selective-serialization"></a><span data-ttu-id="189bb-102">Serialização seletiva</span><span class="sxs-lookup"><span data-stu-id="189bb-102">Selective serialization</span></span>
<span data-ttu-id="189bb-103">Uma classe geralmente contém os campos que não devem ser serializados.</span><span class="sxs-lookup"><span data-stu-id="189bb-103">A class often contains fields that shouldn't be serialized.</span></span> <span data-ttu-id="189bb-104">Por exemplo, presuma que uma classe armazene uma ID de thread em uma variável de membro.</span><span class="sxs-lookup"><span data-stu-id="189bb-104">For example, assume a class stores a thread ID in a member variable.</span></span> <span data-ttu-id="189bb-105">Quando a classe é desserializada, o thread que armazenou a ID de quando a classe foi serializada pode não estar mais em execução; portanto, serializar esse valor não faz sentido.</span><span class="sxs-lookup"><span data-stu-id="189bb-105">When the class is deserialized, the thread stored the ID for when the class was serialized might no longer be running; so serializing this value doesn't make sense.</span></span> <span data-ttu-id="189bb-106">Você pode impedir que variáveis de membros sejam serializadas marcando-as com o atributo [NonSerialized](xref:System.NonSerializedAttribute) da maneira a seguir.</span><span class="sxs-lookup"><span data-stu-id="189bb-106">You can prevent member variables from being serialized by marking them with the [NonSerialized](xref:System.NonSerializedAttribute) attribute as follows.</span></span>  
  
```csharp  
[Serializable]  
public class MyObject   
{  
  public int n1;  
  [NonSerialized] public int n2;  
  public String str;  
}  
```

<span data-ttu-id="189bb-107">Se possível, crie um objeto que possa conter dados confidenciais de segurança não serializáveis.</span><span class="sxs-lookup"><span data-stu-id="189bb-107">If possible, make an object that could contain security-sensitive data nonserializable.</span></span> <span data-ttu-id="189bb-108">Se o objeto tiver que ser serializado, aplique o atributo `NonSerialized` em campos específicos que armazenam dados confidenciais.</span><span class="sxs-lookup"><span data-stu-id="189bb-108">If the object must be serialized, apply the `NonSerialized` attribute to specific fields that store sensitive data.</span></span> <span data-ttu-id="189bb-109">Se você não excluir esses campos da serialização, esteja ciente de que os dados que eles armazenam serão expostos em qualquer código que tenha permissão para serializar.</span><span class="sxs-lookup"><span data-stu-id="189bb-109">If you don't exclude these fields from serialization, be aware that the data they store are exposed to any code that has permission to serialize.</span></span> <span data-ttu-id="189bb-110">Para obter mais informações sobre como escrever um código de serialização segura, consulte [Segurança e serialização](../../../docs/framework/misc/security-and-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="189bb-110">For more information about writing secure serialization code, see [Security and Serialization](../../../docs/framework/misc/security-and-serialization.md).</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
## <a name="see-also"></a><span data-ttu-id="189bb-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="189bb-111">See also</span></span>  
 [<span data-ttu-id="189bb-112">Serialização binária</span><span class="sxs-lookup"><span data-stu-id="189bb-112">Binary Serialization</span></span>](binary-serialization.md)  
 [<span data-ttu-id="189bb-113">Serialização XML e SOAP</span><span class="sxs-lookup"><span data-stu-id="189bb-113">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)  
 [<span data-ttu-id="189bb-114">Segurança e serialização</span><span class="sxs-lookup"><span data-stu-id="189bb-114">Security and Serialization</span></span>](../../../docs/framework/misc/security-and-serialization.md)