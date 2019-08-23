---
title: 'Como: usar EdmGen.exe para gerar o modelo e arquivos de mapeamento'
ms.date: 03/30/2017
ms.assetid: 40db462d-2fd2-4cc1-ad86-d280403e63fa
ms.openlocfilehash: 37234d8f0631ea11ea0d9c7d4e8f027a7266814e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69958446"
---
# <a name="how-to-use-edmgenexe-to-generate-the-model-and-mapping-files"></a>Como: usar EdmGen.exe para gerar o modelo e arquivos de mapeamento
Este tópico mostra como usar a ferramenta Gerador de EDM (EdmGen.exe) para gerar os seguintes arquivos com base no banco de dados da escola:  
  
- Um modelo conceitual (um arquivo .csdl).  
  
- Um modelo de armazenamento (um arquivo .ssdl).  
  
- Mapeamento entre os modelos conceituais e de armazenamento (um arquivo .msl).  
  
- Código da camada de objetos no Visual Basic ou C#.  
  
- Exibir arquivos.  
  
 A ferramenta EdmGen.exe usa /mode:FullGeneration para gerar os arquivos listados acima. Para obter mais informações sobre os comandos EdmGen. exe, consulte [EDM Generator (EdmGen. exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md).  
  
 Se você usar EdmGen. exe para gerar o modelo e os arquivos de mapeamento, ainda precisará configurar seu projeto do Visual Studio para [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]usar o. Para obter mais informações, confira [Como: Configurar manualmente um projeto](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))de Entity Framework.  
  
> [!NOTE]
> Um modelo conceitual gerado pelo EdmGen.exe inclui todos os objetos no banco de dados. Se você quiser gerar um modelo conceitual que inclui somente objetos específicos, use o Assistente do Modelo de Dados de Entidade. Para obter mais informações, confira [Como: Use o assistente](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))de modelo de dados de entidade.  
  
### <a name="to-generate-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a>Para gerar o modelo da escola para um projeto do Visual Basic usando EdmGen.exe  
  
1. Crie o banco de dados da escola. Para obter mais informações, consulte [criando o banco de dados de exemplo da escola](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).  
  
2. No prompt de comando, execute o seguinte comando sem quebras de linha:  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:fullgeneration   
    /c:"Data Source=%datasourceserver%; Initial Catalog=School; Integrated Security=SSPI"   
    /project:School /entitycontainer:SchoolEntities /namespace:SchoolModel /language:VB  
    ```  
  
### <a name="to-generate-the-school-model-for-a-c-project-using-edmgenexe"></a>Para gerar o modelo da escola para um projeto do C# usando EdmGen.exe  
  
1. Crie o banco de dados da escola. Para obter mais informações, consulte [criando o banco de dados de exemplo da escola](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).  
  
2. No prompt de comando, execute o seguinte comando sem quebras de linha:  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:fullgeneration   
    /c:"Data Source=%datasourceserver%; Initial Catalog=School; Integrated Security=SSPI"   
    /project:School /entitycontainer:SchoolEntities /namespace:SchoolModel /language:CSharp  
    ```  
  
## <a name="see-also"></a>Consulte também

- [Modelagem e mapeamento](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md)
- [Como: Configurar manualmente um projeto de Entity Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))
- [Como: Pré-gerar exibições para melhorar o desempenho da consulta](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))
- [Ferramentas de Modelo de Dados de Entidade de ADO.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
- [Como: Usar EdmGen. exe para validar arquivos de modelo e de mapeamento](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-validate-model-and-mapping-files.md)
