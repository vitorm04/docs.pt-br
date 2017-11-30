---
title: "Controlando a serialização e a desserialização sem SerializationBinder"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba8dcecf-acc7-467c-939d-021bbac797d4
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: be5faf5e465eeacc190081c22d7bc59c3caf5825
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/28/2017
---
# <a name="controlling-serialization-and-deserialization-with-serializationbinder"></a><span data-ttu-id="73a97-102">Controlando a serialização e a desserialização sem SerializationBinder</span><span class="sxs-lookup"><span data-stu-id="73a97-102">Controlling Serialization and Deserialization with SerializationBinder</span></span>
<span data-ttu-id="73a97-103">Durante a serialização, um formatador transmite as informações necessárias para criar uma instância de um objeto do tipo correto e a versão.</span><span class="sxs-lookup"><span data-stu-id="73a97-103">During serialization, a formatter transmits the information required to create an instance of an object of the correct type and version.</span></span> <span data-ttu-id="73a97-104">Geralmente, essas informações incluem o nome de tipo completo e o nome de assembly do objeto.</span><span class="sxs-lookup"><span data-stu-id="73a97-104">This information generally includes the full type name and assembly name of the object.</span></span> <span data-ttu-id="73a97-105">Por padrão, a desserialização usa essas informações para criar uma instância de um objeto idêntico.</span><span class="sxs-lookup"><span data-stu-id="73a97-105">By default, deserialization uses this information to create an instance of an identical object.</span></span> <span data-ttu-id="73a97-106">Alguns usuários poderão precisar controlar qual classe para serializar e desserializar, ou porque a classe original pode não existir no computador que está executando a desserialização, a classe original foi movido entre assemblies ou uma versão diferente da classe é necessária do servidor e cliente.</span><span class="sxs-lookup"><span data-stu-id="73a97-106">Some users may need to control which class to serialize and deserialize, either because the original class may not exist on the machine performing deserialization, the original class has moved between assemblies, or a different version of the class is required on the server and client.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="73a97-107">[Uso do associador de serialização](../../../../docs/framework/wcf/samples/usage-of-serialization-binder.md).</span><span class="sxs-lookup"><span data-stu-id="73a97-107"> [Usage of Serialization Binder](../../../../docs/framework/wcf/samples/usage-of-serialization-binder.md).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="73a97-108">Essa funcionalidade está disponível somente ao usar o <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> ou <xref:System.Runtime.Serialization.NetDataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="73a97-108">This functionality is only available when using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> or the <xref:System.Runtime.Serialization.NetDataContractSerializer>.</span></span>  
  
## <a name="using-serializationbinder"></a><span data-ttu-id="73a97-109">Usando SerializationBinder</span><span class="sxs-lookup"><span data-stu-id="73a97-109">Using SerializationBinder</span></span>  
 <span data-ttu-id="73a97-110">O <xref:System.Runtime.Serialization.SerializationBinder> é uma classe abstrata usada para controlar os tipos reais usados durante a serialização e a desserialização.</span><span class="sxs-lookup"><span data-stu-id="73a97-110"><xref:System.Runtime.Serialization.SerializationBinder> is an abstract class used to control the actual types used during serialization and deserialization.</span></span> <span data-ttu-id="73a97-111">Para controlar os tipos usados durante a serialização e desserialização, derive uma classe de <xref:System.Runtime.Serialization.SerializationBinder> e substituir o <xref:System.Runtime.Serialization.SerializationBinder.BindToName(System.Type,System.String@,System.String@)> e <xref:System.Runtime.Serialization.SerializationBinder.BindToType(System.String,System.String)> métodos.</span><span class="sxs-lookup"><span data-stu-id="73a97-111">To control the types used during serialization and deserialization, derive a class from <xref:System.Runtime.Serialization.SerializationBinder> and override the <xref:System.Runtime.Serialization.SerializationBinder.BindToName(System.Type,System.String@,System.String@)> and <xref:System.Runtime.Serialization.SerializationBinder.BindToType(System.String,System.String)> methods.</span></span> <span data-ttu-id="73a97-112">O <xref:System.Runtime.Serialization.SerializationBinder.BindToName(System.Type,System.String@,System.String@)> leva um <xref:System.Type> e retorna um nome de assembly e tipo.</span><span class="sxs-lookup"><span data-stu-id="73a97-112">The <xref:System.Runtime.Serialization.SerializationBinder.BindToName(System.Type,System.String@,System.String@)> method takes a <xref:System.Type> and returns an assembly and type name.</span></span> <span data-ttu-id="73a97-113">O <xref:System.Runtime.Serialization.SerializationBinder.BindToType(System.String,System.String)> usa um nome de assembly e o tipo de método e retorna um <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="73a97-113">The <xref:System.Runtime.Serialization.SerializationBinder.BindToType(System.String,System.String)> method takes an assembly and type name and returns a <xref:System.Type>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73a97-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="73a97-114">See Also</span></span>  
 [<span data-ttu-id="73a97-115">Serialização e desserialização</span><span class="sxs-lookup"><span data-stu-id="73a97-115">Serialization and Deserialization</span></span>](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md)  
 [<span data-ttu-id="73a97-116">Uso do associador de serialização</span><span class="sxs-lookup"><span data-stu-id="73a97-116">Usage of Serialization Binder</span></span>](../../../../docs/framework/wcf/samples/usage-of-serialization-binder.md)
