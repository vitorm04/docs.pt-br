---
title: 'Como: Use EdmGen.exe para gerar código de objetos camada'
ms.date: 03/30/2017
ms.assetid: c44d2ebe-f66f-42cb-9741-4a3f0c2dcffb
ms.openlocfilehash: c15ceec66ad5b1c9ef414c3e57e3b6e49c372e7a
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43416258"
---
# <a name="how-to-use-edmgenexe-to-generate-object-layer-code"></a><span data-ttu-id="4e4a6-102">Como: Use EdmGen.exe para gerar código de objetos camada</span><span class="sxs-lookup"><span data-stu-id="4e4a6-102">How to: Use EdmGen.exe to Generate Object-Layer Code</span></span>
<span data-ttu-id="4e4a6-103">Este tópico mostra como usar o [gerador de EDM (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md) ferramenta para gerar o código da camada de objeto com base em arquivo. CSDL.</span><span class="sxs-lookup"><span data-stu-id="4e4a6-103">This topic shows how to use the [EDM Generator (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md) tool to generate object-layer code  based on the .csdl file.</span></span>  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a><span data-ttu-id="4e4a6-104">Para gerar código de objetos camada para o modelo de escola para um projeto Visual Basic usando EdmGen.exe</span><span class="sxs-lookup"><span data-stu-id="4e4a6-104">To generate object-layer code for the School model for a Visual Basic project using EdmGen.exe</span></span>  
  
1.  <span data-ttu-id="4e4a6-105">Crie o banco de dados da escola.</span><span class="sxs-lookup"><span data-stu-id="4e4a6-105">Create the School database.</span></span> <span data-ttu-id="4e4a6-106">Para obter mais informações, consulte [criando o banco de dados de exemplo School](https://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0).</span><span class="sxs-lookup"><span data-stu-id="4e4a6-106">For more information, see [Creating the School Sample Database](https://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0).</span></span>  
  
2.  <span data-ttu-id="4e4a6-107">Gerencia o modelo de escola ou obter o arquivo de School.csdl.</span><span class="sxs-lookup"><span data-stu-id="4e4a6-107">Generate the School model or obtain the School.csdl file.</span></span> <span data-ttu-id="4e4a6-108">Para obter mais informações, consulte [como: Use EdmGen.exe para gerar arquivos de modelo e mapeamento](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="4e4a6-108">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
3.  <span data-ttu-id="4e4a6-109">No prompt de comando, execute o seguinte comando sem quebras de linha:</span><span class="sxs-lookup"><span data-stu-id="4e4a6-109">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration   
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.vb /language:VB  
    ```  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-c-project-using-edmgenexe"></a><span data-ttu-id="4e4a6-110">Para gerar código de objetos camada para o modelo de escola para um projeto C# usando EdmGen.exe</span><span class="sxs-lookup"><span data-stu-id="4e4a6-110">To generate object-layer code for the School model for a C# project using EdmGen.exe</span></span>  
  
1.  <span data-ttu-id="4e4a6-111">Crie o banco de dados da escola.</span><span class="sxs-lookup"><span data-stu-id="4e4a6-111">Create the School database.</span></span> <span data-ttu-id="4e4a6-112">Para obter mais informações, consulte [criando o banco de dados de exemplo School](https://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0).</span><span class="sxs-lookup"><span data-stu-id="4e4a6-112">For more information, see [Creating the School Sample Database](https://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0).</span></span>  
  
2.  <span data-ttu-id="4e4a6-113">Gerencia o modelo de escola ou obter o arquivo de School.csdl.</span><span class="sxs-lookup"><span data-stu-id="4e4a6-113">Generate the School model or obtain the School.csdl file.</span></span> <span data-ttu-id="4e4a6-114">Para obter mais informações, consulte [como: Use EdmGen.exe para gerar arquivos de modelo e mapeamento](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="4e4a6-114">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
3.  <span data-ttu-id="4e4a6-115">No prompt de comando, execute o seguinte comando sem quebras de linha:</span><span class="sxs-lookup"><span data-stu-id="4e4a6-115">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration   
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.cs /language:CSharp  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="4e4a6-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4e4a6-116">See Also</span></span>  
 [<span data-ttu-id="4e4a6-117">Modelagem e mapeamento</span><span class="sxs-lookup"><span data-stu-id="4e4a6-117">Modeling and Mapping</span></span>](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md)  
 [<span data-ttu-id="4e4a6-118">Como: configurar manualmente um projeto do Entity Framework</span><span class="sxs-lookup"><span data-stu-id="4e4a6-118">How to: Manually Configure an Entity Framework Project</span></span>](https://msdn.microsoft.com/library/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e)  
 <span data-ttu-id="4e4a6-119">[ADO.NET Entity Data Model Tools](https://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527) (Ferramentas de modelo de dados de entidade do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="4e4a6-119">[ADO.NET Entity Data Model  Tools](https://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527)</span></span>  
 [<span data-ttu-id="4e4a6-120">Como: gerar previamente exibições para melhorar o desempenho de consulta</span><span class="sxs-lookup"><span data-stu-id="4e4a6-120">How to: Pre-Generate Views to Improve Query Performance</span></span>](https://msdn.microsoft.com/library/b18a9d16-e10b-4043-ba91-b632f85a2579)  
 [<span data-ttu-id="4e4a6-121">Como usar o EdmGen.exe para gerar o modelo e os arquivos de mapeamento</span><span class="sxs-lookup"><span data-stu-id="4e4a6-121">How to: Use EdmGen.exe to Generate the Model and Mapping Files</span></span>](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)
