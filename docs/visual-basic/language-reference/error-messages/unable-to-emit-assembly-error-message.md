---
title: 'Não foi possível emitir o assembly: <error message>'
ms.date: 08/14/2018
f1_keywords:
- vbc30145
- bc30145
helpviewer_keywords:
- BC30145
ms.assetid: 2e7eb2b9-eda6-4bdb-95cc-72c7f0be7528
ms.openlocfilehash: 5776755a57fbc2b0086b1c9b6cfbb2f2b7eb03fa
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197267"
---
# <a name="unable-to-emit-assembly-error-message"></a>Não é possível emitir o assembly: \<mensagem de erro >

O compilador Visual Basic chama o vinculador do assembly (*al. exe*, também conhecido como ALink) para gerar um assembly com um manifesto, e o vinculador relata um erro no estágio de emissão da criação do assembly.

**ID do erro:** BC30145

## <a name="to-correct-this-error"></a>Para corrigir este erro

1. Examine a mensagem de erro entre aspas e consulte o tópico [al. exe](../../../framework/tools/al-exe-assembly-linker.md) para obter mais explicações e conselhos.

2. Tente assinar o assembly manualmente, usando o [al. exe](../../../framework/tools/al-exe-assembly-linker.md) ou a [ferramenta sn. exe (Strong Name)](../../../framework/tools/sn-exe-strong-name-tool.md).

3. Se o erro persistir, reúna informações sobre as circunstâncias e notifique o Microsoft Product Support Services.

### <a name="to-sign-the-assembly-manually"></a>Para assinar o assembly manualmente

1. Use o [sn. exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)para criar um arquivo de par de chaves pública/privada.

   Este arquivo tem uma extensão *. SNK* .

2. Exclua a referência COM que está gerando o erro no projeto.

3. Abra o [prompt de comando do desenvolvedor para o Visual Studio](../../../framework/tools/developer-command-prompt-for-vs.md).

   No Windows 10, insira o **prompt de comando do desenvolvedor** na caixa de pesquisa na barra de tarefas. Em seguida, selecione **prompt de comando do desenvolvedor para VS 2017** na lista de resultados.

4. Altere o diretório para o diretório onde você deseja posicionar o seu wrapper de assembly.

5. Insira o seguinte comando:

    ```cmd
    tlbimp <path to COM reference file> /out:<output assembly name> /keyfile:<path to .snk file>
    ```

   Um exemplo do comando real que você pode inserir é:

    ```cmd
    tlbimp c:\windows\system32\msi.dll /out:Interop.WindowsInstaller.dll /keyfile:"c:\documents and settings\mykey.snk"
    ```

   > [!TIP]
   > Use aspas duplas se um caminho ou arquivo contiver espaços.

6. No Visual Studio, adicione uma referência de assembly .NET ao arquivo que você acabou de criar.

## <a name="see-also"></a>Consulte também

- [Al. exe](../../../framework/tools/al-exe-assembly-linker.md)
- [Sn.exe (Ferramenta Nome Forte)](../../../framework/tools/sn-exe-strong-name-tool.md)
- [Como criar um par de chaves pública/privada](../../../standard/assembly/create-public-private-key-pair.md)
- [Fale conosco](/visualstudio/ide/feedback-options)
