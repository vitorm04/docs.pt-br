---
title: 'Como: Use EdmGen.exe para validar o modelo e arquivos de mapeamento'
ms.date: 03/30/2017
ms.assetid: 2641906a-971a-4d0b-8aee-13fabc02a1cc
ms.openlocfilehash: fda8698381e98c64318f1a26f77f0263e9085074
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43512439"
---
# <a name="how-to-use-edmgenexe-to-validate-model-and-mapping-files"></a>Como: Use EdmGen.exe para validar o modelo e arquivos de mapeamento
Este tópico mostra como usar o [gerador de EDM (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md) ferramenta para validar o modelo e arquivos de mapeamento. Para obter mais informações, consulte [modelo de dados de entidade](../../../../../docs/framework/data/adonet/entity-data-model.md).  
  
### <a name="to-validate-the-school-model-using-edmgenexe"></a>Para validar a escola EdmGen.exe do modelo  
  
1.  Crie o banco de dados da escola. Para obter mais informações, consulte [criando o banco de dados de exemplo School](https://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0).  
  
2.  Gerencia o modelo de escola. Para obter mais informações, consulte [como: Use EdmGen.exe para gerar arquivos de modelo e mapeamento](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).  
  
3.  No prompt de comando, execute o seguinte comando sem quebras de linha:  
  
    ```console
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:ValidateArtifacts /inssdl:.\School.ssdl /inmsl:.\School.msl /incsdl:.\School.csdl  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Como: configurar manualmente um projeto do Entity Framework](https://msdn.microsoft.com/library/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e)  
 [ADO.NET Entity Data Model Tools](https://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527) (Ferramentas de modelo de dados de entidade do ADO.NET)  
 [Como: gerar previamente exibições para melhorar o desempenho de consulta](https://msdn.microsoft.com/library/b18a9d16-e10b-4043-ba91-b632f85a2579)  
 [Como usar o EdmGen.exe para gerar o código da camada de objeto](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-object-layer-code.md)
