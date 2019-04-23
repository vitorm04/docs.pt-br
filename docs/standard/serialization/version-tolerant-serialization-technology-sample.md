---
title: Exemplo de tecnologia de serialização básica tolerante a versões
ms.date: 03/30/2017
ms.assetid: 2a183664-bfbf-4ff0-96f6-c836284ea916
ms.openlocfilehash: d7dfcf7548571d29032495ca8be96db70f2336fc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59308349"
---
# <a name="version-tolerant-serialization-technology-sample"></a>Exemplo de tecnologia de serialização básica tolerante a versões
[Baixar Exemplo](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Runtime%20Serialization/VTS.zip.exe)  
  
 Esse exemplo demonstra os recursos de tolerância de versão da Serialização .NET. O exemplo cria aplicativos que usam versões diferentes de um <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> para serializar e desserializar dados. Apesar da presença de diferentes versões de tipo, os aplicativos se comunicam de maneira simplificada. Para obter mais informações, consulte [Serialização tolerante a versão](../../../docs/standard/serialization/version-tolerant-serialization.md).  
  
### <a name="to-build-the-sample-using-the-command-prompt"></a>Para criar o exemplo usando o prompt de comando  
  
1. Abra uma janela do Prompt de Comando e navegue para um dos subdiretórios específicos da linguagem (em V1 Application ou V2 Application) para o exemplo.  
  
2. Digite **msbuild.exe \<ver> application.sln** na linha de comando (em que \<ver> é v1 ou v2).  
  
### <a name="to-build-the-sample-using-visual-studio"></a>Para criar o exemplo usando Visual Studio  
  
1. Abra o [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] e navegue para um dos subdiretórios específicos da linguagem para o exemplo.  
  
2. Navegue para o subdiretório V1 Application do diretório que você selecionou na etapa anterior.  
  
3. Clique duas vezes no ícone para V1 Application.sln para abrir o arquivo no Visual Studio.  
  
4. No menu **Compilar**, clique em **Compilar Solução**.  
  
5. Navegue para o subdiretório V2 Application e repita as duas etapas anteriores para criar o V2 Application.  
  
 Os aplicativos serão criados nos subdiretórios padrão \bin ou \bin\Debug de seus respectivos diretórios de projeto.  
  
### <a name="to-run-the-sample"></a>Para executar a amostra  
  
1. Na uma janela do Prompt de Comando, navegue para o subdiretório específico da linguagem que você selecionou ao criar os aplicativos de exemplo.  
  
2. Digite **runme.cmd** na linha de comando para executar ambos os aplicativos de uma vez.  
  
 Como alternativa, navegue para os diretórios que contêm os novos executáveis e execute-os sequencialmente.  
  
> [!NOTE]
>  O exemplo cria aplicativos de console. Você deve lançá-los e executá-los em uma janela do prompt de comando para exibir sua saída.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>
- <xref:System.IO.FileStream>
