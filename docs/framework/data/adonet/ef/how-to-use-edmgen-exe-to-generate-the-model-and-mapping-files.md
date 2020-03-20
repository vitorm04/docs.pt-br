---
title: Como usar EdmGen.exe para gerar o modelo e arquivos de mapeamento
ms.date: 03/30/2017
ms.assetid: 40db462d-2fd2-4cc1-ad86-d280403e63fa
ms.openlocfilehash: ee8297c0833378b2b44800355b47db9caa2dc7fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150501"
---
# <a name="how-to-use-edmgenexe-to-generate-the-model-and-mapping-files"></a>Como usar EdmGen.exe para gerar o modelo e arquivos de mapeamento
Este tópico mostra como usar a ferramenta Gerador de EDM (EdmGen.exe) para gerar os seguintes arquivos com base no banco de dados da escola:  
  
- Um modelo conceitual (um arquivo .csdl).  
  
- Um modelo de armazenamento (um arquivo .ssdl).  
  
- Mapeamento entre os modelos conceituais e de armazenamento (um arquivo .msl).  
  
- Código da camada de objetos no Visual Basic ou C#.  
  
- Exibir arquivos.  
  
 A ferramenta EdmGen.exe usa /mode:FullGeneration para gerar os arquivos listados acima. Para obter mais informações sobre os comandos EdmGen.exe, consulte [EDM Generator (EdmGen.exe)](edm-generator-edmgen-exe.md).  
  
 Se você usar o EdmGen.exe para gerar o modelo e os arquivos de mapeamento, você ainda precisa configurar seu projeto visual studio para usar o Framework entity. Para obter mais informações, [consulte Como configurar manualmente um projeto-quadro de entidades](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100)).  
  
> [!NOTE]
> Um modelo conceitual gerado pelo EdmGen.exe inclui todos os objetos no banco de dados. Se você quiser gerar um modelo conceitual que inclui somente objetos específicos, use o Assistente do Modelo de Dados de Entidade. Para obter mais informações, consulte [Como: Usar o Assistente do Modelo de Dados da Entidade](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).  
  
### <a name="to-generate-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a>Para gerar o modelo da escola para um projeto do Visual Basic usando EdmGen.exe  
  
1. Crie o banco de dados da escola. Para obter mais informações, consulte [Criando o Banco de Dados de Amostras Escolares](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).  
  
2. No prompt de comando, execute o seguinte comando sem quebras de linha:  
  
    ```console  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:fullgeneration
    /c:"Data Source=%datasourceserver%; Initial Catalog=School; Integrated Security=SSPI"
    /project:School /entitycontainer:SchoolEntities /namespace:SchoolModel /language:VB  
    ```  
  
### <a name="to-generate-the-school-model-for-a-c-project-using-edmgenexe"></a>Para gerar o modelo da escola para um projeto do C# usando EdmGen.exe  
  
1. Crie o banco de dados da escola. Para obter mais informações, consulte [Criando o Banco de Dados de Amostras Escolares](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).  
  
2. No prompt de comando, execute o seguinte comando sem quebras de linha:  
  
    ```console  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:fullgeneration
    /c:"Data Source=%datasourceserver%; Initial Catalog=School; Integrated Security=SSPI"
    /project:School /entitycontainer:SchoolEntities /namespace:SchoolModel /language:CSharp  
    ```  
  
## <a name="see-also"></a>Confira também

- [Modelando e mapeando](modeling-and-mapping.md)
- [Como: Configurar manualmente um projeto-quadro de entidades](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))
- [Como: Pré-gerar visualizações para melhorar o desempenho da consulta](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))
- [ADO.NET ferramentas de modelo de dados de entidades](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
- [Como: Use EdmGen.exe para validar o modelo e arquivos de mapeamento](how-to-use-edmgen-exe-to-validate-model-and-mapping-files.md)
