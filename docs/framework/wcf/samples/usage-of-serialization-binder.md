---
title: Utilização do associador de serialização
ms.date: 03/30/2017
ms.assetid: ab46c087-200c-45bf-9c95-5a6cda6e8b98
ms.openlocfilehash: 677decebcf444fed95311bd02acf8a96e0a4eca9
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591770"
---
# <a name="usage-of-serialization-binder"></a><span data-ttu-id="83747-102">Utilização do associador de serialização</span><span class="sxs-lookup"><span data-stu-id="83747-102">Usage of Serialization Binder</span></span>
<span data-ttu-id="83747-103">Este exemplo mostra como usar o <xref:System.Runtime.Serialization.SerializationBinder> para alterar a versão de um tipo genérico quando ele é serializado.</span><span class="sxs-lookup"><span data-stu-id="83747-103">This sample shows how to use the <xref:System.Runtime.Serialization.SerializationBinder> to change the version of a generic type when it is serialized.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="83747-104">Demonstra</span><span class="sxs-lookup"><span data-stu-id="83747-104">Demonstrates</span></span>  
 <span data-ttu-id="83747-105"><xref:System.Runtime.Serialization.SerializationBinder>, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter></span><span class="sxs-lookup"><span data-stu-id="83747-105"><xref:System.Runtime.Serialization.SerializationBinder>, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter></span></span>  
  
## <a name="discussion"></a><span data-ttu-id="83747-106">Discussão</span><span class="sxs-lookup"><span data-stu-id="83747-106">Discussion</span></span>  
 <span data-ttu-id="83747-107">Este exemplo mostra como duas entidades que são direcionamento de versões diferentes podem do .NET Framework se comunicar usando o formatador binário e o associador de serialização.</span><span class="sxs-lookup"><span data-stu-id="83747-107">This sample shows how two entities that are targeting different versions of the .NET Framework can communicate using the binary formatter and the serialization binder.</span></span>  
  
 <span data-ttu-id="83747-108">O desenvolvimento deste exemplo foi realizado usando a comunicação remota do .NET.</span><span class="sxs-lookup"><span data-stu-id="83747-108">The development of this sample has been done using .NET Remoting.</span></span> <span data-ttu-id="83747-109">O exemplo consiste em um servidor de direcionamento [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)], que implementa um contrato com tipos genéricos e dois clientes diferentes, um direcionamento [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)] e o direcionamento de outro [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="83747-109">The sample consists of a server targeting [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)], which implements a contract with generic types, and two different clients, one targeting [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)] and another targeting [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)].</span></span>  
  
 <span data-ttu-id="83747-110">As conexões de servidor um <xref:System.Runtime.Serialization.SerializationBinder> ao formatador binário para poder alterar a versão dos tipos de acordo sobre serialização, portanto, ambos os clientes podem desserializar esses tipos corretamente.</span><span class="sxs-lookup"><span data-stu-id="83747-110">The server attaches a <xref:System.Runtime.Serialization.SerializationBinder> to the binary formatter to be able to change the version of the types accordingly on serialization, so both clients can deserialize those types properly.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="83747-111">Para configurar, compilar e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="83747-111">To set up, build and run the sample</span></span>  
  
1. <span data-ttu-id="83747-112">Para executar o cliente, clique com botão direito a solução, SBGenericsVTS (6 projetos) e, em seguida, selecione **propriedades**.</span><span class="sxs-lookup"><span data-stu-id="83747-112">To execute the client, right-click the solution, SBGenericsVTS (6 projects) and then select **Properties**.</span></span>  
  
2. <span data-ttu-id="83747-113">Na **propriedades comuns**, selecione **projeto de inicialização**, em seguida, selecione **vários projetos de inicialização**.</span><span class="sxs-lookup"><span data-stu-id="83747-113">In **Common Properties**, select **Startup Project**, then select **Multiple Startup Projects**.</span></span>  
  
3. <span data-ttu-id="83747-114">Selecione **Server** , em seguida, primeiro **Client20** e, em seguida, **Client40**.</span><span class="sxs-lookup"><span data-stu-id="83747-114">Select **Server** first, then **Client20** and then **Client40**.</span></span> <span data-ttu-id="83747-115">Selecione o **inicie** ação para esses três projetos e deixe o restante definido como **None**.</span><span class="sxs-lookup"><span data-stu-id="83747-115">Select the **Start** action to these three projects and leave the rest set to **None**.</span></span>  
  
4. <span data-ttu-id="83747-116">Clique em **Okey** e, em seguida, pressione F5 para executar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="83747-116">Click **OK** and then press F5 to run the sample.</span></span>
