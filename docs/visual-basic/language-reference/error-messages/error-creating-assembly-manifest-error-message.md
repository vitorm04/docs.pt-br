---
title: 'Erro ao criar o manifesto do assembly: &lt;mensagem de erro&gt; | Documentos do Microsoft'
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30140
- vbc30140
dev_langs:
- VB
helpviewer_keywords:
- BC30140
ms.assetid: 1beb5aa0-7b79-4c85-946b-5c2d0a41d1d2
caps.latest.revision: 13
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 35a912bbcab78178ce636afa550c244823da512c
ms.lasthandoff: 03/13/2017

---
# <a name="error-creating-assembly-manifest-lterror-messagegt"></a>Erro ao criar o manifesto do assembly: &lt;mensagem de erro&gt;
O compilador [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] chama o Assembly Linker (Al.exe, também conhecido como Alink) para gerar um assembly com um manifesto. O vinculador reportou um erro no estágio de pré-emissão da criação do assembly.  
  
 Isso pode ocorrer se houver problemas com o arquivo de chave ou o contêiner de chave especificado. Para marcar totalmente um assembly, é necessário fornecer um arquivo de chave válido que contenha informações sobre as chaves públicas e privadas. Para atrasar a assinatura de um assembly, você deve selecionar o **atrasar a assinatura somente** caixa de seleção e forneça um arquivo de chave válido que contém informações sobre as informações da chave públicas. A chave privada não é necessária quando um assembly estiver marcado com atraso. Para obter mais informações, consulte [como: assinar um Assembly (Visual Studio)](http://msdn.microsoft.com/en-us/f468a7d3-234c-4353-924d-8e0ae5896564).  
  
 **ID do erro:** BC30140  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Examine a mensagem de erro entre aspas e consulte o tópico [Al.exe Tool Errors and Warnings](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b) para o erro AL1019 mais explicações e conselhos  
  
2.  Se o erro persistir, reúna informações sobre as circunstâncias e notifique o Microsoft Product Support Services.  
  
## <a name="see-also"></a>Consulte também  
 [Como assinar um assembly (Visual Studio)](http://msdn.microsoft.com/en-us/f468a7d3-234c-4353-924d-8e0ae5896564)   
 [Página Assinatura, Designer de Projeto](https://docs.microsoft.com/visualstudio/ide/reference/signing-page-project-designer)   
 [Al.exe (Assembly Linker)](https://msdn.microsoft.com/library/c405shex)   
 [Ferramenta de Al.exe erros e avisos](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b)   
 [Fale conosco](https://docs.microsoft.com/visualstudio/ide/talk-to-us)
