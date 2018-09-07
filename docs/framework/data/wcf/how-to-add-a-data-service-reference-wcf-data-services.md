---
title: 'Como: adicionar uma referência de serviço de dados (WCF Data Services)'
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 62c6f318-3ee1-433a-b7a3-efa234c3034c
ms.openlocfilehash: fc1786e1c6102c702374989253cd3ce23e3f7b54
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44084631"
---
# <a name="how-to-add-a-data-service-reference-wcf-data-services"></a><span data-ttu-id="7f1b7-102">Como: adicionar uma referência de serviço de dados (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="7f1b7-102">How to: Add a data service reference (WCF Data Services)</span></span>

<span data-ttu-id="7f1b7-103">Você pode usar o **adicionar referência de serviço** caixa de diálogo no Visual Studio para adicionar uma referência para o WCF Data Services.</span><span class="sxs-lookup"><span data-stu-id="7f1b7-103">You can use the **Add Service Reference** dialog in Visual Studio to add a reference to WCF Data Services.</span></span> <span data-ttu-id="7f1b7-104">Isso permite que você acesse mais facilmente um serviço de dados em um aplicativo cliente que você desenvolve no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7f1b7-104">This enables you to more easily access a data service in a client application that you develop in Visual Studio.</span></span> <span data-ttu-id="7f1b7-105">Quando você concluir este procedimento, as classes de dados são geradas com base nos metadados que é obtido do serviço de dados.</span><span class="sxs-lookup"><span data-stu-id="7f1b7-105">When you complete this procedure, data classes are generated based on metadata that is obtained from the data service.</span></span> <span data-ttu-id="7f1b7-106">Para obter mais informações, consulte [gerando a biblioteca de cliente do serviço de dados](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="7f1b7-106">For more information, see [Generating the Data Service Client Library](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md).</span></span>

## <a name="add-a-data-service-reference"></a><span data-ttu-id="7f1b7-107">Adicionar uma referência de serviço de dados</span><span class="sxs-lookup"><span data-stu-id="7f1b7-107">Add a data service reference</span></span>

1. <span data-ttu-id="7f1b7-108">(Opcional) Se o serviço de dados não é parte da solução e não já está em execução, inicie o serviço de dados e observe o URI do serviço de dados.</span><span class="sxs-lookup"><span data-stu-id="7f1b7-108">(Optional) If the data service is not part of the solution and is not already running, start the data service and note the URI of the data service.</span></span>

2. <span data-ttu-id="7f1b7-109">No Visual Studio, no **Gerenciador de soluções**, o projeto de cliente com o botão direito e, em seguida, selecione **Add** > **referência de serviço**.</span><span class="sxs-lookup"><span data-stu-id="7f1b7-109">In Visual Studio, in **Solution Explorer**, right-click the client project and then select **Add** > **Service Reference**.</span></span>

3. <span data-ttu-id="7f1b7-110">Se o serviço de dados é parte da solução atual, clique em **Discover**.</span><span class="sxs-lookup"><span data-stu-id="7f1b7-110">If the data service is part of the current solution, click **Discover**.</span></span>

     <span data-ttu-id="7f1b7-111">-ou-</span><span class="sxs-lookup"><span data-stu-id="7f1b7-111">-or-</span></span>

     <span data-ttu-id="7f1b7-112">No **endereço** caixa de texto, digite a URL base do serviço de dados, como `http://localhost:1234/Northwind.svc`e, em seguida, clique em **vá**.</span><span class="sxs-lookup"><span data-stu-id="7f1b7-112">In the **Address** text box, type the base URL of the data service, such as `http://localhost:1234/Northwind.svc`, and then click **Go**.</span></span>

4. <span data-ttu-id="7f1b7-113">Selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="7f1b7-113">Select **OK**.</span></span>

     <span data-ttu-id="7f1b7-114">Um novo arquivo de código que contém as classes de dados que podem acessar e interagir com os recursos do serviço de dados é adicionado ao projeto.</span><span class="sxs-lookup"><span data-stu-id="7f1b7-114">A new code file that contains the data classes that can access and interact with data service resources is added to the project.</span></span>

## <a name="see-also"></a><span data-ttu-id="7f1b7-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7f1b7-115">See also</span></span>

- <span data-ttu-id="7f1b7-116">[Quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md) (Início rápido)</span><span class="sxs-lookup"><span data-stu-id="7f1b7-116">[Quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)</span></span>