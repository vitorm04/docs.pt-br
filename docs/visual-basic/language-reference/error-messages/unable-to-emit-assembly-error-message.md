---
title: 'Não é possível emitir o assembly: &lt;mensagem de erro&gt;'
ms.date: 07/20/2015
f1_keywords:
- vbc30145
- bc30145
helpviewer_keywords:
- BC30145
ms.assetid: 2e7eb2b9-eda6-4bdb-95cc-72c7f0be7528
ms.openlocfilehash: 8f497069088ad30a3be58d02caa0a32f7f1b21b7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33595167"
---
# <a name="unable-to-emit-assembly-lterror-messagegt"></a>Não é possível emitir o assembly: &lt;mensagem de erro&gt;
O compilador do Visual Basic chama o Assembly Linker (Al.exe, também conhecido como Alink) para gerar um assembly com um manifesto, com o vinculador relatar um erro no estágio de emissão de criar o assembly.  
  
 **ID do erro:** BC30145  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Examine a mensagem de erro citada e consulte o tópico [Al.exe](../../../framework/tools/al-exe-assembly-linker.md). Para obter mais explicações e conselhos.  
  
2.  Tente assinar o assembly manualmente, usando o [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) ou [Sn.exe (ferramenta de nome forte)](../../../framework/tools/sn-exe-strong-name-tool.md).  
  
3.  Se o erro persistir, reúna informações sobre as circunstâncias e notifique o Microsoft Product Support Services.  
  
### <a name="to-sign-the-assembly-manually"></a>Para assinar o assembly manualmente  
  
1.  Use o [Sn.exe (ferramenta de nome forte)][Sn.exe (ferramenta de nome forte)](../../../framework/tools/sn-exe-strong-name-tool.md)) para criar um arquivo de par de chaves pública/privada.  
  
     Esse arquivo tem a extensão .snk.  
  
2.  Exclua a referência COM que está gerando o erro no projeto.  
  
3.  Do Windows **iniciar** , aponte para **programas**, aponte para **Microsoft Visual Studio 2008**, aponte para **ferramentas do Visual Studio**, e em seguida, clique em **Prompt de comando do Visual Studio 2008**.  
  
4.  Acesse o diretório onde deseja colocar o wrapper do assembly.  
  
5.  Digite o código a seguir.  
  
    ```  
    tlbimp <path to COM reference file> /out:<output assembly name> /keyfile:<path to .snk file>  
    ```  
  
     Um exemplo do código que pode ser inserido seria o seguinte.  
  
    ```  
    tlbimp c:\windows\system32\msi.dll /out:Interop.WindowsInstaller.dll /keyfile:"c:\documents and settings\mykey.snk"  
    ```  
  
     Use aspas duplas (") se um caminho ou arquivo contiver espaços.  
  
6.  No Visual Studio, adicione uma referência de Assembly do .NET para o arquivo que você acabou de criar.  
  
## <a name="see-also"></a>Consulte também  
 
 [Al.exe](../../../framework/tools/al-exe-assembly-linker.md).  
 [Sn.exe (ferramenta de nome forte)] [Sn.exe (ferramenta de nome forte)](../../../framework/tools/sn-exe-strong-name-tool.md))  
 [Como criar um par de chaves pública/privada](../../../framework/app-domains/how-to-create-a-public-private-key-pair.md)  
 [Fale conosco](/visualstudio/ide/talk-to-us)
