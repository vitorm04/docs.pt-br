---
title: 'Como: usar EdmGen.exe para gerar código de objetos camada'
ms.date: 03/30/2017
ms.assetid: c44d2ebe-f66f-42cb-9741-4a3f0c2dcffb
ms.openlocfilehash: a243a588dcb6f7e7001de331cb9011a23ee2fdbe
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198217"
---
# <a name="how-to-use-edmgenexe-to-generate-object-layer-code"></a>Como: usar EdmGen.exe para gerar código de objetos camada

Este tópico mostra como usar a ferramenta [gerador de EDM (EdmGen.exe)](edm-generator-edmgen-exe.md) para gerar o código de camada de objeto com base no arquivo. CSDL.  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a>Para gerar código de objetos camada para o modelo de escola para um projeto Visual Basic usando EdmGen.exe  
  
1. Crie o banco de dados da escola. Para obter mais informações, consulte [criando o banco de dados de exemplo da escola](/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).  
  
2. Gerencia o modelo de escola ou obter o arquivo de School.csdl. Para obter mais informações, consulte [como: usar EdmGen.exe para gerar o modelo e os arquivos de mapeamento](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).  
  
3. No prompt de comando, execute o seguinte comando sem quebras de linha:  
  
    ```console  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.vb /language:VB  
    ```  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-c-project-using-edmgenexe"></a>Para gerar código de objetos camada para o modelo de escola para um projeto C# usando EdmGen.exe  
  
1. Crie o banco de dados da escola. Para obter mais informações, consulte [criando o banco de dados de exemplo da escola](/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).  
  
2. Gerencia o modelo de escola ou obter o arquivo de School.csdl. Para obter mais informações, consulte [como: usar EdmGen.exe para gerar o modelo e os arquivos de mapeamento](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).  
  
3. No prompt de comando, execute o seguinte comando sem quebras de linha:  
  
    ```console  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.cs /language:CSharp  
    ```  
  
## <a name="see-also"></a>Veja também

- [Modelando e mapeando](modeling-and-mapping.md)
- [Como configurar manualmente um projeto de Entity Framework](/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))
- [ADO.NET Entity Data Model Tools](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100)) (Ferramentas de modelo de dados de entidade do ADO.NET)
- [Como: gerar previamente modos de exibição para melhorar o desempenho da consulta](/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))
- [Como: usar EdmGen.exe para gerar o modelo e arquivos de mapeamento](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)
