---
title: 'Como: adicionar uma referência de serviço de dados (WCF Data Services)'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 62c6f318-3ee1-433a-b7a3-efa234c3034c
ms.openlocfilehash: a8dcc01fb7a564a363cabed6a22738cd520d317f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33356225"
---
# <a name="how-to-add-a-data-service-reference-wcf-data-services"></a><span data-ttu-id="26ff1-102">Como: adicionar uma referência de serviço de dados (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="26ff1-102">How to: Add a Data Service Reference (WCF Data Services)</span></span>
<span data-ttu-id="26ff1-103">Você pode usar o **adicionar referência de serviço** caixa de diálogo no Visual Studio para adicionar uma referência a [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].</span><span class="sxs-lookup"><span data-stu-id="26ff1-103">You can use the **Add Service Reference** dialog in Visual Studio to add a reference to [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].</span></span> <span data-ttu-id="26ff1-104">Isso permite que você acesse mais facilmente um serviço de dados em um aplicativo cliente que você desenvolver no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="26ff1-104">This enables you to more easily access a data service in a client application that you develop in Visual Studio.</span></span> <span data-ttu-id="26ff1-105">Quando você concluir este procedimento, classes de dados são gerados com base nos metadados que é obtido do serviço de dados.</span><span class="sxs-lookup"><span data-stu-id="26ff1-105">When you complete this procedure, data classes are generated based on metadata that is obtained from the data service.</span></span> <span data-ttu-id="26ff1-106">Para obter mais informações, consulte [gerando a biblioteca de cliente do serviço de dados](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="26ff1-106">For more information, see [Generating the Data Service Client Library](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md).</span></span>  
  
### <a name="to-add-a-data-service-reference"></a><span data-ttu-id="26ff1-107">Para adicionar uma referência de serviço de dados</span><span class="sxs-lookup"><span data-stu-id="26ff1-107">To add a data service reference</span></span>  
  
1.  <span data-ttu-id="26ff1-108">(Opcional) Se o serviço de dados não faz parte da solução e não está sendo executado, inicie o serviço de dados e observe o URI do serviço de dados.</span><span class="sxs-lookup"><span data-stu-id="26ff1-108">(Optional) If the data service is not part of the solution and is not already running, start the data service and note the URI of the data service.</span></span>  
  
2.  <span data-ttu-id="26ff1-109">O projeto de cliente e, em seguida, selecione **adicionar referência de serviço**.</span><span class="sxs-lookup"><span data-stu-id="26ff1-109">Right-click the client project and then select **Add Service Reference**.</span></span>  
  
3.  <span data-ttu-id="26ff1-110">Se o serviço de dados é parte da solução atual, clique em **Discover**.</span><span class="sxs-lookup"><span data-stu-id="26ff1-110">If the data service is part of the current solution, click **Discover**.</span></span>  
  
     <span data-ttu-id="26ff1-111">-ou-</span><span class="sxs-lookup"><span data-stu-id="26ff1-111">-or-</span></span>  
  
     <span data-ttu-id="26ff1-112">No **endereço** caixa de texto, digite a URL base do serviço de dados, como `http://localhost:1234/Northwind.svc`e, em seguida, clique em **vá**.</span><span class="sxs-lookup"><span data-stu-id="26ff1-112">In the **Address** text box, type the base URL of the data service, such as `http://localhost:1234/Northwind.svc`, and then click **Go**.</span></span>  
  
4.  <span data-ttu-id="26ff1-113">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="26ff1-113">Click **OK**.</span></span>  
  
     <span data-ttu-id="26ff1-114">Isso adiciona um novo arquivo de código que contém as classes de dados que são usadas para acessar e interagir com os recursos de serviço de dados como objetos.</span><span class="sxs-lookup"><span data-stu-id="26ff1-114">This adds a new code file that contains the data classes that are used to access and interact with data service resources as objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26ff1-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="26ff1-115">See Also</span></span>  
 <span data-ttu-id="26ff1-116">[Quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md) (Início rápido)</span><span class="sxs-lookup"><span data-stu-id="26ff1-116">[Quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)</span></span>
