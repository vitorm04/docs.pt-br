---
title: "Não é possível emitir o assembly: &lt;mensagem de erro&gt; | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30145
- bc30145
dev_langs:
- VB
helpviewer_keywords:
- BC30145
ms.assetid: 2e7eb2b9-eda6-4bdb-95cc-72c7f0be7528
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: dac4b133882c043f9c84e936bad2e36f35fc4c33
ms.lasthandoff: 03/13/2017

---
# <a name="unable-to-emit-assembly-lterror-messagegt"></a>Não é possível emitir o assembly: &lt;mensagem de erro&gt;
O compilador [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] chama o Assembly Linker (Al.exe, também conhecido como Alink) para gerar um assembly com um manifesto, com o vinculador relatando um erro no estágio de emissão da criação do assembly.  
  
 **ID do erro:** BC30145  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Examine a mensagem de erro entre aspas e consulte o tópico [Al.exe Tool Errors and Warnings](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b) para obter mais explicações e conselhos.  
  
2.  Tente assinar o assembly manualmente, usando o [Al.exe (Assembly Linker)](https://msdn.microsoft.com/library/c405shex) ou [Sn.exe (ferramenta de nome forte)](https://msdn.microsoft.com/library/k5b5tt23).  
  
3.  Se o erro persistir, reúna informações sobre as circunstâncias e notifique o Microsoft Product Support Services.  
  
### <a name="to-sign-the-assembly-manually"></a>Para assinar o assembly manualmente  
  
1.  Use o [Sn.exe (ferramenta de nome forte)](https://msdn.microsoft.com/library/k5b5tt23) para criar um arquivo de par de chaves pública/privada.  
  
     Esse arquivo tem a extensão .snk.  
  
2.  Exclua a referência COM que está gerando o erro no projeto.  
  
3.  Do Windows **iniciar** , aponte para **programas**, aponte para **Microsoft Visual Studio 2008**, aponte para **Visual Studio Tools**e, em seguida, clique em **Prompt de comando do Visual Studio 2008**.  
  
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
  
6.  Em [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)], inclua uma referência .NET Assembly para o arquivo que acabou de ser criado.  
  
## <a name="see-also"></a>Consulte também  
 [Al.exe (Assembly Linker)](https://msdn.microsoft.com/library/c405shex)   
 [Ferramenta de Al.exe erros e avisos](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b)   
 [Sn.exe (ferramenta de nome forte)](https://msdn.microsoft.com/library/k5b5tt23)   
 [Como criar um par de chaves pública/privada](http://msdn.microsoft.com/library/05026813-f3bd-4d7c-9e0b-fc588eb3d114)   
 [Fale conosco](https://docs.microsoft.com/visualstudio/ide/talk-to-us)
