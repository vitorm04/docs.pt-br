---
title: "Não é possível emitir o assembly: &lt;mensagem de erro&gt;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30145
- bc30145
helpviewer_keywords:
- BC30145
ms.assetid: 2e7eb2b9-eda6-4bdb-95cc-72c7f0be7528
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b19b6439d85822c69adac0b3e0e04b2f31299836
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="unable-to-emit-assembly-lterror-messagegt"></a>Não é possível emitir o assembly: &lt;mensagem de erro&gt;
O compilador [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] chama o Assembly Linker (Al.exe, também conhecido como Alink) para gerar um assembly com um manifesto, com o vinculador relatando um erro no estágio de emissão da criação do assembly.  
  
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
  
6.  Em [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)], inclua uma referência .NET Assembly para o arquivo que acabou de ser criado.  
  
## <a name="see-also"></a>Consulte também  
 
 [Al.exe](../../../framework/tools/al-exe-assembly-linker.md).  
 [Sn.exe (ferramenta de nome forte)] [Sn.exe (ferramenta de nome forte)](../../../framework/tools/sn-exe-strong-name-tool.md))  
 [Como criar um par de chaves pública/privada](../../../framework/app-domains/how-to-create-a-public-private-key-pair.md)  
 [Fale conosco](/visualstudio/ide/talk-to-us)
