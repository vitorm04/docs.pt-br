---
title: "Utilização do associador de serialização"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ab46c087-200c-45bf-9c95-5a6cda6e8b98
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: be6ce62722c0d1bd18122496312c3a55241a8fbb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="usage-of-serialization-binder"></a><span data-ttu-id="23f41-102">Utilização do associador de serialização</span><span class="sxs-lookup"><span data-stu-id="23f41-102">Usage of Serialization Binder</span></span>
<span data-ttu-id="23f41-103">Este exemplo mostra como usar o <xref:System.Runtime.Serialization.SerializationBinder> para alterar a versão de um tipo genérico quando ele é serializado.</span><span class="sxs-lookup"><span data-stu-id="23f41-103">This sample shows how to use the <xref:System.Runtime.Serialization.SerializationBinder> to change the version of a generic type when it is serialized.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="23f41-104">Demonstra</span><span class="sxs-lookup"><span data-stu-id="23f41-104">Demonstrates</span></span>  
 <span data-ttu-id="23f41-105"><xref:System.Runtime.Serialization.SerializationBinder>, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter></span><span class="sxs-lookup"><span data-stu-id="23f41-105"><xref:System.Runtime.Serialization.SerializationBinder>, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter></span></span>  
  
## <a name="discussion"></a><span data-ttu-id="23f41-106">Discussão</span><span class="sxs-lookup"><span data-stu-id="23f41-106">Discussion</span></span>  
 <span data-ttu-id="23f41-107">Este exemplo mostra como duas entidades que são destinados a versões diferentes do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] podem se comunicar usando o formatador binário e o associador de serialização.</span><span class="sxs-lookup"><span data-stu-id="23f41-107">This sample shows how two entities that are targeting different versions of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] can communicate using the binary formatter and the serialization binder.</span></span>  
  
 <span data-ttu-id="23f41-108">O desenvolvimento deste exemplo foi realizado usando a comunicação remota do .NET.</span><span class="sxs-lookup"><span data-stu-id="23f41-108">The development of this sample has been done using .NET Remoting.</span></span> <span data-ttu-id="23f41-109">O exemplo consiste em um servidor de destino [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)], que implementa um contrato com tipos genéricos e dois clientes diferentes, um direcionamento [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)] e o direcionamento de outro [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="23f41-109">The sample consists of a server targeting [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)], which implements a contract with generic types, and two different clients, one targeting [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)] and another targeting [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)].</span></span>  
  
 <span data-ttu-id="23f41-110">As conexões de servidor um <xref:System.Runtime.Serialization.SerializationBinder> para o formatador binário para poder alterar a versão dos tipos adequadamente na serialização, então ambos os clientes podem desserializar esses tipos corretamente.</span><span class="sxs-lookup"><span data-stu-id="23f41-110">The server attaches a <xref:System.Runtime.Serialization.SerializationBinder> to the binary formatter to be able to change the version of the types accordingly on serialization, so both clients can deserialize those types properly.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="23f41-111">Para configurar, compilar e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="23f41-111">To set up, build and run the sample</span></span>  
  
1.  <span data-ttu-id="23f41-112">Para executar o cliente, clique com botão direito a solução, SBGenericsVTS (6 projetos) e, em seguida, selecione **propriedades**.</span><span class="sxs-lookup"><span data-stu-id="23f41-112">To execute the client, right-click the solution, SBGenericsVTS (6 projects) and then select **Properties**.</span></span>  
  
2.  <span data-ttu-id="23f41-113">Em **propriedades comuns**, selecione **projeto de inicialização**, em seguida, selecione **vários projetos de inicialização**.</span><span class="sxs-lookup"><span data-stu-id="23f41-113">In **Common Properties**, select **Startup Project**, then select **Multiple Startup Projects**.</span></span>  
  
3.  <span data-ttu-id="23f41-114">Selecione **servidor** primeiro, em seguida, **Client20** e **Client40**.</span><span class="sxs-lookup"><span data-stu-id="23f41-114">Select **Server** first, then **Client20** and then **Client40**.</span></span> <span data-ttu-id="23f41-115">Selecione o **iniciar** ação para esses três projetos e deixe o resto definido como **nenhum**.</span><span class="sxs-lookup"><span data-stu-id="23f41-115">Select the **Start** action to these three projects and leave the rest set to **None**.</span></span>  
  
4.  <span data-ttu-id="23f41-116">Clique em **Okey** e, em seguida, pressione F5 para executar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="23f41-116">Click **OK** and then press F5 to run the sample.</span></span>
