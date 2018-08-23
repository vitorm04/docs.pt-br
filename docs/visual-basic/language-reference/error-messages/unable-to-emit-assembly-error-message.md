---
title: 'Não foi possível emitir o assembly: <error message>'
ms.date: 08/14/2018
f1_keywords:
- vbc30145
- bc30145
helpviewer_keywords:
- BC30145
ms.assetid: 2e7eb2b9-eda6-4bdb-95cc-72c7f0be7528
ms.openlocfilehash: 404a8255adcdc414a40b40395ada1c90c1078325
ms.sourcegitcommit: a1e35d4e94edab384a63406c0a5438306873031b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2018
ms.locfileid: "42754130"
---
# <a name="unable-to-emit-assembly-error-message"></a>Não é possível emitir o assembly: \<mensagem de erro >

O compilador do Visual Basic chama o Assembly Linker (*Al.exe*, também conhecido como Alink) gerar um assembly com um manifesto e o vinculador relata um erro no estágio de emissão da criação do assembly.

**ID do erro:** BC30145

## <a name="to-correct-this-error"></a>Para corrigir este erro

1. Examine a mensagem de erro entre aspas e consulte o tópico [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) para obter mais explicações e conselhos.

2. Tente assinar o assembly manualmente, usando o [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) ou o [Sn.exe (ferramenta de nome forte)](../../../framework/tools/sn-exe-strong-name-tool.md).

3. Se o erro persistir, reúna informações sobre as circunstâncias e notifique o Microsoft Product Support Services.

### <a name="to-sign-the-assembly-manually"></a>Para assinar o assembly manualmente

1. Use o [Sn.exe (ferramenta de nome forte)](../../../framework/tools/sn-exe-strong-name-tool.md)) para criar um arquivo de par de chaves pública/privada.

   Esse arquivo tem um *. snk* extensão.

2. Exclua a referência COM que está gerando o erro no projeto.

3. Abra o [Prompt de comando do desenvolvedor para Visual Studio](../../../framework/tools/developer-command-prompt-for-vs.md).

   No Windows 10, insira **prompt de comando do desenvolvedor** na caixa de pesquisa na barra de tarefas. Em seguida, selecione **Prompt de comando do desenvolvedor para VS 2017** na lista de resultados.

4. Altere o diretório para o diretório onde você deseja colocar o wrapper do assembly.

5. Insira o seguinte comando:

    ```cmd
    tlbimp <path to COM reference file> /out:<output assembly name> /keyfile:<path to .snk file>
    ```

   É um exemplo do comando real que você pode inserir:

    ```cmd
    tlbimp c:\windows\system32\msi.dll /out:Interop.WindowsInstaller.dll /keyfile:"c:\documents and settings\mykey.snk"
    ```

   > [!TIP]
   > Se um arquivo ou o caminho contiver espaços, use aspas duplas.

6. No Visual Studio, adicione uma referência de Assembly do .NET para o arquivo que você acabou de criar.

## <a name="see-also"></a>Consulte também

- [Al.exe](../../../framework/tools/al-exe-assembly-linker.md).
- [Sn.exe (ferramenta nome forte)] [Sn.exe (ferramenta nome forte)](../../../framework/tools/sn-exe-strong-name-tool.md))
- [Como criar um par de chaves pública/privada](../../../framework/app-domains/how-to-create-a-public-private-key-pair.md)
- [Fale conosco](/visualstudio/ide/talk-to-us)