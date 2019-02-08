---
title: 'Como: Use EdmGen.exe para gerar o código da camada de objeto'
ms.date: 03/30/2017
ms.assetid: c44d2ebe-f66f-42cb-9741-4a3f0c2dcffb
ms.openlocfilehash: 4acc60f324d41ed23ad3ef63907b031f003b07c1
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55827144"
---
# <a name="how-to-use-edmgenexe-to-generate-object-layer-code"></a><span data-ttu-id="a58d4-102">Como: Use EdmGen.exe para gerar o código da camada de objeto</span><span class="sxs-lookup"><span data-stu-id="a58d4-102">How to: Use EdmGen.exe to Generate Object-Layer Code</span></span>
<span data-ttu-id="a58d4-103">Este tópico mostra como usar o [gerador de EDM (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md) ferramenta para gerar o código da camada de objeto com base em arquivo. CSDL.</span><span class="sxs-lookup"><span data-stu-id="a58d4-103">This topic shows how to use the [EDM Generator (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md) tool to generate object-layer code  based on the .csdl file.</span></span>  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a><span data-ttu-id="a58d4-104">Para gerar código de objetos camada para o modelo de escola para um projeto Visual Basic usando EdmGen.exe</span><span class="sxs-lookup"><span data-stu-id="a58d4-104">To generate object-layer code for the School model for a Visual Basic project using EdmGen.exe</span></span>  
  
1.  <span data-ttu-id="a58d4-105">Crie o banco de dados da escola.</span><span class="sxs-lookup"><span data-stu-id="a58d4-105">Create the School database.</span></span> <span data-ttu-id="a58d4-106">Para obter mais informações, consulte [criando o banco de dados de exemplo School](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="a58d4-106">For more information, see [Creating the School Sample Database](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span></span>  
  
2.  <span data-ttu-id="a58d4-107">Gerencia o modelo de escola ou obter o arquivo de School.csdl.</span><span class="sxs-lookup"><span data-stu-id="a58d4-107">Generate the School model or obtain the School.csdl file.</span></span> <span data-ttu-id="a58d4-108">Para obter mais informações, confira [Como: Use EdmGen.exe para gerar o modelo e arquivos de mapeamento](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="a58d4-108">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
3.  <span data-ttu-id="a58d4-109">No prompt de comando, execute o seguinte comando sem quebras de linha:</span><span class="sxs-lookup"><span data-stu-id="a58d4-109">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration   
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.vb /language:VB  
    ```  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-c-project-using-edmgenexe"></a><span data-ttu-id="a58d4-110">Para gerar código de objetos camada para o modelo de escola para um projeto C# usando EdmGen.exe</span><span class="sxs-lookup"><span data-stu-id="a58d4-110">To generate object-layer code for the School model for a C# project using EdmGen.exe</span></span>  
  
1.  <span data-ttu-id="a58d4-111">Crie o banco de dados da escola.</span><span class="sxs-lookup"><span data-stu-id="a58d4-111">Create the School database.</span></span> <span data-ttu-id="a58d4-112">Para obter mais informações, consulte [criando o banco de dados de exemplo School](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="a58d4-112">For more information, see [Creating the School Sample Database](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span></span>  
  
2.  <span data-ttu-id="a58d4-113">Gerencia o modelo de escola ou obter o arquivo de School.csdl.</span><span class="sxs-lookup"><span data-stu-id="a58d4-113">Generate the School model or obtain the School.csdl file.</span></span> <span data-ttu-id="a58d4-114">Para obter mais informações, confira [Como: Use EdmGen.exe para gerar o modelo e arquivos de mapeamento](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="a58d4-114">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
3.  <span data-ttu-id="a58d4-115">No prompt de comando, execute o seguinte comando sem quebras de linha:</span><span class="sxs-lookup"><span data-stu-id="a58d4-115">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration   
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.cs /language:CSharp  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="a58d4-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a58d4-116">See also</span></span>
- [<span data-ttu-id="a58d4-117">Modelagem e mapeamento</span><span class="sxs-lookup"><span data-stu-id="a58d4-117">Modeling and Mapping</span></span>](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md)
- <span data-ttu-id="a58d4-118">[Como: Configurar manualmente um projeto do Entity Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a58d4-118">[How to: Manually Configure an Entity Framework Project](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))</span></span>
- <span data-ttu-id="a58d4-119">[ADO.NET Entity Data Model Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100)) (Ferramentas de modelo de dados de entidade do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="a58d4-119">[ADO.NET Entity Data Model  Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>
- <span data-ttu-id="a58d4-120">[Como: Gerar previamente exibições para melhorar o desempenho de consulta](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a58d4-120">[How to: Pre-Generate Views to Improve Query Performance](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))</span></span>
- [<span data-ttu-id="a58d4-121">Como: Use EdmGen.exe para gerar o modelo e arquivos de mapeamento</span><span class="sxs-lookup"><span data-stu-id="a58d4-121">How to: Use EdmGen.exe to Generate the Model and Mapping Files</span></span>](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)
