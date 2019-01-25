---
title: 'Como: Use EdmGen.exe para validar o modelo e arquivos de mapeamento'
ms.date: 03/30/2017
ms.assetid: 2641906a-971a-4d0b-8aee-13fabc02a1cc
ms.openlocfilehash: 87150aee8eac6a594b18b77230889c1208003dde
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54566353"
---
# <a name="how-to-use-edmgenexe-to-validate-model-and-mapping-files"></a><span data-ttu-id="87fa7-102">Como: Use EdmGen.exe para validar o modelo e arquivos de mapeamento</span><span class="sxs-lookup"><span data-stu-id="87fa7-102">How to: Use EdmGen.exe to Validate Model and Mapping Files</span></span>
<span data-ttu-id="87fa7-103">Este tópico mostra como usar o [gerador de EDM (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md) ferramenta para validar o modelo e arquivos de mapeamento.</span><span class="sxs-lookup"><span data-stu-id="87fa7-103">This topic shows how to use the [EDM Generator (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md) tool to validate the model and mapping files.</span></span> <span data-ttu-id="87fa7-104">Para obter mais informações, consulte [modelo de dados de entidade](../../../../../docs/framework/data/adonet/entity-data-model.md).</span><span class="sxs-lookup"><span data-stu-id="87fa7-104">For more information, see [Entity Data Model](../../../../../docs/framework/data/adonet/entity-data-model.md).</span></span>  
  
### <a name="to-validate-the-school-model-using-edmgenexe"></a><span data-ttu-id="87fa7-105">Para validar a escola EdmGen.exe do modelo</span><span class="sxs-lookup"><span data-stu-id="87fa7-105">To validate the School model using EdmGen.exe</span></span>  
  
1.  <span data-ttu-id="87fa7-106">Crie o banco de dados da escola.</span><span class="sxs-lookup"><span data-stu-id="87fa7-106">Create the School database.</span></span> <span data-ttu-id="87fa7-107">Para obter mais informações, consulte [criando o banco de dados de exemplo School](https://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0).</span><span class="sxs-lookup"><span data-stu-id="87fa7-107">For more information, see [Creating the School Sample Database](https://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0).</span></span>  
  
2.  <span data-ttu-id="87fa7-108">Gerencia o modelo de escola.</span><span class="sxs-lookup"><span data-stu-id="87fa7-108">Generate the School model.</span></span> <span data-ttu-id="87fa7-109">Para obter mais informações, confira [Como: Use EdmGen.exe para gerar o modelo e arquivos de mapeamento](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="87fa7-109">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
3.  <span data-ttu-id="87fa7-110">No prompt de comando, execute o seguinte comando sem quebras de linha:</span><span class="sxs-lookup"><span data-stu-id="87fa7-110">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```console
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:ValidateArtifacts /inssdl:.\School.ssdl /inmsl:.\School.msl /incsdl:.\School.csdl  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="87fa7-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="87fa7-111">See also</span></span>
- [<span data-ttu-id="87fa7-112">Como: Configurar manualmente um projeto do Entity Framework</span><span class="sxs-lookup"><span data-stu-id="87fa7-112">How to: Manually Configure an Entity Framework Project</span></span>](https://msdn.microsoft.com/library/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e)
- <span data-ttu-id="87fa7-113">[ADO.NET Entity Data Model Tools](https://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527) (Ferramentas de modelo de dados de entidade do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="87fa7-113">[ADO.NET Entity Data Model  Tools](https://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527)</span></span>
- [<span data-ttu-id="87fa7-114">Como: Gerar previamente exibições para melhorar o desempenho de consulta</span><span class="sxs-lookup"><span data-stu-id="87fa7-114">How to: Pre-Generate Views to Improve Query Performance</span></span>](https://msdn.microsoft.com/library/b18a9d16-e10b-4043-ba91-b632f85a2579)
- [<span data-ttu-id="87fa7-115">Como: Use EdmGen.exe para gerar o código da camada de objeto</span><span class="sxs-lookup"><span data-stu-id="87fa7-115">How to: Use EdmGen.exe to Generate Object-Layer Code</span></span>](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-object-layer-code.md)
