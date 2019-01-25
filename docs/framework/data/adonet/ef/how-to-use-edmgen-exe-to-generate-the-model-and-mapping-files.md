---
title: 'Como: Use EdmGen.exe para gerar o modelo e arquivos de mapeamento'
ms.date: 03/30/2017
ms.assetid: 40db462d-2fd2-4cc1-ad86-d280403e63fa
ms.openlocfilehash: 340ef0b20c25ca76df51085592e53849c6bf7a12
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54610147"
---
# <a name="how-to-use-edmgenexe-to-generate-the-model-and-mapping-files"></a>Como: Use EdmGen.exe para gerar o modelo e arquivos de mapeamento
Este tópico mostra como usar a ferramenta Gerador de EDM (EdmGen.exe) para gerar os seguintes arquivos com base no banco de dados da escola:  
  
-   Um modelo conceitual (um arquivo .csdl).  
  
-   Um modelo de armazenamento (um arquivo .ssdl).  
  
-   Mapeamento entre os modelos conceituais e de armazenamento (um arquivo .msl).  
  
-   Código da camada de objetos no Visual Basic ou C#.  
  
-   Exibir arquivos.  
  
 A ferramenta EdmGen.exe usa /mode:FullGeneration para gerar os arquivos listados acima. Para obter mais informações sobre comandos EdmGen.exe, consulte [gerador de EDM (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md).  
  
 Se você usar EdmGen.exe para gerar o modelo e arquivos de mapeamento, você ainda precisará configurar seu projeto do Visual Studio para usar o [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Para obter mais informações, confira [Como: Configurar manualmente um projeto do Entity Framework](https://msdn.microsoft.com/library/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e).  
  
> [!NOTE]
>  Um modelo conceitual gerado pelo EdmGen.exe inclui todos os objetos no banco de dados. Se você quiser gerar um modelo conceitual que inclui somente objetos específicos, use o Assistente do Modelo de Dados de Entidade. Para obter mais informações, confira [Como: Use o Assistente de modelo de dados de entidade](https://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).  
  
### <a name="to-generate-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a>Para gerar o modelo da escola para um projeto do Visual Basic usando EdmGen.exe  
  
1.  Crie o banco de dados da escola. Para obter mais informações, consulte [criando o banco de dados de exemplo School](https://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0).  
  
2.  No prompt de comando, execute o seguinte comando sem quebras de linha:  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:fullgeneration   
    /c:"Data Source=%datasourceserver%; Initial Catalog=School; Integrated Security=SSPI"   
    /project:School /entitycontainer:SchoolEntities /namespace:SchoolModel /language:VB  
    ```  
  
### <a name="to-generate-the-school-model-for-a-c-project-using-edmgenexe"></a>Para gerar o modelo da escola para um projeto do C# usando EdmGen.exe  
  
1.  Crie o banco de dados da escola. Para obter mais informações, consulte [criando o banco de dados de exemplo School](https://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0).  
  
2.  No prompt de comando, execute o seguinte comando sem quebras de linha:  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:fullgeneration   
    /c:"Data Source=%datasourceserver%; Initial Catalog=School; Integrated Security=SSPI"   
    /project:School /entitycontainer:SchoolEntities /namespace:SchoolModel /language:CSharp  
    ```  
  
## <a name="see-also"></a>Consulte também
- [Modelagem e mapeamento](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md)
- [Como: Configurar manualmente um projeto do Entity Framework](https://msdn.microsoft.com/library/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e)
- [Como: Gerar previamente exibições para melhorar o desempenho de consulta](https://msdn.microsoft.com/library/b18a9d16-e10b-4043-ba91-b632f85a2579)
- [ADO.NET Entity Data Model Tools](https://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527) (Ferramentas de modelo de dados de entidade do ADO.NET)
- [Como: Use EdmGen.exe para validar o modelo e arquivos de mapeamento](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-validate-model-and-mapping-files.md)
