---
title: 'Como: Adicionar uma referência de serviço de dados (WCF Data Services)'
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 62c6f318-3ee1-433a-b7a3-efa234c3034c
ms.openlocfilehash: 42d89cf87b5fe9bbdb229f10cd6a0e340d4c08fd
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790743"
---
# <a name="how-to-add-a-data-service-reference-wcf-data-services"></a><span data-ttu-id="16871-102">Como: Adicionar uma referência de serviço de dados (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="16871-102">How to: Add a data service reference (WCF Data Services)</span></span>

<span data-ttu-id="16871-103">Você pode usar a caixa de diálogo **Adicionar referência de serviço** no Visual Studio para adicionar uma referência a WCF Data Services.</span><span class="sxs-lookup"><span data-stu-id="16871-103">You can use the **Add Service Reference** dialog in Visual Studio to add a reference to WCF Data Services.</span></span> <span data-ttu-id="16871-104">Isso permite que você acesse mais facilmente um serviço de dados em um aplicativo cliente que você desenvolve no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="16871-104">This enables you to more easily access a data service in a client application that you develop in Visual Studio.</span></span> <span data-ttu-id="16871-105">Quando você concluir este procedimento, as classes de dados serão geradas com base nos metadados obtidos do serviço de dados.</span><span class="sxs-lookup"><span data-stu-id="16871-105">When you complete this procedure, data classes are generated based on metadata that is obtained from the data service.</span></span> <span data-ttu-id="16871-106">Para obter mais informações, consulte [gerando a biblioteca de cliente do serviço de dados](generating-the-data-service-client-library-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="16871-106">For more information, see [Generating the Data Service Client Library](generating-the-data-service-client-library-wcf-data-services.md).</span></span>

## <a name="add-a-data-service-reference"></a><span data-ttu-id="16871-107">Adicionar uma referência de serviço de dados</span><span class="sxs-lookup"><span data-stu-id="16871-107">Add a data service reference</span></span>

1. <span data-ttu-id="16871-108">Adicional Se o serviço de dados não fizer parte da solução e ainda não estiver em execução, inicie o serviço de dados e anote o URI do serviço de dados.</span><span class="sxs-lookup"><span data-stu-id="16871-108">(Optional) If the data service is not part of the solution and is not already running, start the data service and note the URI of the data service.</span></span>

2. <span data-ttu-id="16871-109">No Visual Studio, em **Gerenciador de soluções**, clique com o botão direito do mouse no projeto cliente e selecione **Adicionar** > **referência de serviço**.</span><span class="sxs-lookup"><span data-stu-id="16871-109">In Visual Studio, in **Solution Explorer**, right-click the client project and then select **Add** > **Service Reference**.</span></span>

3. <span data-ttu-id="16871-110">Se o serviço de dados fizer parte da solução atual, clique em **descobrir**.</span><span class="sxs-lookup"><span data-stu-id="16871-110">If the data service is part of the current solution, click **Discover**.</span></span>

     <span data-ttu-id="16871-111">- ou -</span><span class="sxs-lookup"><span data-stu-id="16871-111">-or-</span></span>

     <span data-ttu-id="16871-112">Na caixa de texto **endereço** , digite a URL base do serviço de dados, `http://localhost:1234/Northwind.svc`como e clique em **ir**.</span><span class="sxs-lookup"><span data-stu-id="16871-112">In the **Address** text box, type the base URL of the data service, such as `http://localhost:1234/Northwind.svc`, and then click **Go**.</span></span>

4. <span data-ttu-id="16871-113">Selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="16871-113">Select **OK**.</span></span>

     <span data-ttu-id="16871-114">Um novo arquivo de código que contém as classes de dados que podem acessar e interagir com os recursos do serviço de dados é adicionado ao projeto.</span><span class="sxs-lookup"><span data-stu-id="16871-114">A new code file that contains the data classes that can access and interact with data service resources is added to the project.</span></span>

## <a name="see-also"></a><span data-ttu-id="16871-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="16871-115">See also</span></span>

- <span data-ttu-id="16871-116">[Quickstart](quickstart-wcf-data-services.md) (Início rápido)</span><span class="sxs-lookup"><span data-stu-id="16871-116">[Quickstart](quickstart-wcf-data-services.md)</span></span>
