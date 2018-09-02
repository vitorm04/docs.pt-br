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
# <a name="how-to-use-edmgenexe-to-generate-object-layer-code"></a>Como: Use EdmGen.exe para gerar código de objetos camada
Este tópico mostra como usar o [gerador de EDM (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md) ferramenta para gerar o código da camada de objeto com base em arquivo. CSDL.  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a>Para gerar código de objetos camada para o modelo de escola para um projeto Visual Basic usando EdmGen.exe  
  
1.  Crie o banco de dados da escola. Para obter mais informações, consulte [criando o banco de dados de exemplo School](https://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0).  
  
2.  Gerencia o modelo de escola ou obter o arquivo de School.csdl. Para obter mais informações, consulte [como: Use EdmGen.exe para gerar arquivos de modelo e mapeamento](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).  
  
3.  No prompt de comando, execute o seguinte comando sem quebras de linha:  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration   
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.vb /language:VB  
    ```  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-c-project-using-edmgenexe"></a>Para gerar código de objetos camada para o modelo de escola para um projeto C# usando EdmGen.exe  
  
1.  Crie o banco de dados da escola. Para obter mais informações, consulte [criando o banco de dados de exemplo School](https://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0).  
  
2.  Gerencia o modelo de escola ou obter o arquivo de School.csdl. Para obter mais informações, consulte [como: Use EdmGen.exe para gerar arquivos de modelo e mapeamento](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).  
  
3.  No prompt de comando, execute o seguinte comando sem quebras de linha:  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration   
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.cs /language:CSharp  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Modelagem e mapeamento](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md)  
 [Como: configurar manualmente um projeto do Entity Framework](https://msdn.microsoft.com/library/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e)  
 [ADO.NET Entity Data Model Tools](https://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527) (Ferramentas de modelo de dados de entidade do ADO.NET)  
 [Como: gerar previamente exibições para melhorar o desempenho de consulta](https://msdn.microsoft.com/library/b18a9d16-e10b-4043-ba91-b632f85a2579)  
 [Como usar o EdmGen.exe para gerar o modelo e os arquivos de mapeamento](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)
