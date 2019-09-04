---
title: 'Como: usar EdmGen.exe para validar o modelo e arquivos de mapeamento'
ms.date: 03/30/2017
ms.assetid: 2641906a-971a-4d0b-8aee-13fabc02a1cc
ms.openlocfilehash: 4495ff3c5d55779e9db113a2a59361b643841382
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251374"
---
# <a name="how-to-use-edmgenexe-to-validate-model-and-mapping-files"></a><span data-ttu-id="09f6f-102">Como: usar EdmGen.exe para validar o modelo e arquivos de mapeamento</span><span class="sxs-lookup"><span data-stu-id="09f6f-102">How to: Use EdmGen.exe to Validate Model and Mapping Files</span></span>
<span data-ttu-id="09f6f-103">Este tópico mostra como usar a ferramenta do [gerador EDM (EdmGen. exe)](edm-generator-edmgen-exe.md) para validar o modelo e os arquivos de mapeamento.</span><span class="sxs-lookup"><span data-stu-id="09f6f-103">This topic shows how to use the [EDM Generator (EdmGen.exe)](edm-generator-edmgen-exe.md) tool to validate the model and mapping files.</span></span> <span data-ttu-id="09f6f-104">Para obter mais informações, consulte [modelo de dados de entidade](../entity-data-model.md).</span><span class="sxs-lookup"><span data-stu-id="09f6f-104">For more information, see [Entity Data Model](../entity-data-model.md).</span></span>  
  
### <a name="to-validate-the-school-model-using-edmgenexe"></a><span data-ttu-id="09f6f-105">Para validar a escola EdmGen.exe do modelo</span><span class="sxs-lookup"><span data-stu-id="09f6f-105">To validate the School model using EdmGen.exe</span></span>  
  
1. <span data-ttu-id="09f6f-106">Crie o banco de dados da escola.</span><span class="sxs-lookup"><span data-stu-id="09f6f-106">Create the School database.</span></span> <span data-ttu-id="09f6f-107">Para obter mais informações, consulte [criando o banco de dados de exemplo da escola](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="09f6f-107">For more information, see [Creating the School Sample Database](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="09f6f-108">Gerencia o modelo de escola.</span><span class="sxs-lookup"><span data-stu-id="09f6f-108">Generate the School model.</span></span> <span data-ttu-id="09f6f-109">Para obter mais informações, confira [Como: Use EdmGen. exe para gerar o modelo e os arquivos](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)de mapeamento.</span><span class="sxs-lookup"><span data-stu-id="09f6f-109">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
3. <span data-ttu-id="09f6f-110">No prompt de comando, execute o seguinte comando sem quebras de linha:</span><span class="sxs-lookup"><span data-stu-id="09f6f-110">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```console
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:ValidateArtifacts /inssdl:.\School.ssdl /inmsl:.\School.msl /incsdl:.\School.csdl  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="09f6f-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="09f6f-111">See also</span></span>

- <span data-ttu-id="09f6f-112">[Como: Configurar manualmente um projeto de Entity Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="09f6f-112">[How to: Manually Configure an Entity Framework Project](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))</span></span>
- <span data-ttu-id="09f6f-113">[Ferramentas de Modelo de Dados de Entidade de ADO.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="09f6f-113">[ADO.NET Entity Data Model Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>
- <span data-ttu-id="09f6f-114">[Como: Pré-gerar exibições para melhorar o desempenho da consulta](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="09f6f-114">[How to: Pre-Generate Views to Improve Query Performance](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))</span></span>
- [<span data-ttu-id="09f6f-115">Como: Use EdmGen. exe para gerar código de camada de objeto</span><span class="sxs-lookup"><span data-stu-id="09f6f-115">How to: Use EdmGen.exe to Generate Object-Layer Code</span></span>](how-to-use-edmgen-exe-to-generate-object-layer-code.md)
