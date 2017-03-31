---
title: "Como configurar variáveis de ambiente para a linha de comando do Visual Studio | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- cs.build.commandline
dev_langs:
- CSharp
helpviewer_keywords:
- csc.exe, command-line builds
- Visual C#, command-line builds
- command-line compilers, Visual C#
- Vsvars32.bat
- builds [C#], command-line
- compilers, invoking from command line
- Vcvars32.bat file
- command line [C#], building from
- Visual C# compiler, enabling
- compiling source code, from command line
ms.assetid: 7ec09480-5612-4f6a-8d00-ad90ea9bca5d
caps.latest.revision: 15
author: BillWagner
ms.author: wiwagn
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: e2cc644bb3b2c51615fe763224505b07e113ad62
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-set-environment-variables-for-the-visual-studio-command-line"></a>Como: configurar variáveis de ambiente para a linha de comando do Visual Studio
O arquivo vsvars32.bat define as variáveis de ambiente adequadas para habilitar builds de linha de comando. Para obter mais informações sobre vsvars32.bat, consulte [Knowledge Base article Q248802 (Artigo da base de dados de conhecimento Q248802)](http://go.microsoft.com/fwlink/?LinkId=225042).  
  
 Se a versão atual do Visual Studio estiver instalada em um computador que também tem uma versão anterior do Visual Studio, você não deverá executar vsvars32.bat ou vcvars32.bat das versões diferentes na mesma janela do Prompt de Comando.  
  
### <a name="to-run-vsvars32bat"></a>Para executar VSVARS32.BAT  
  
1.  No menu **Iniciar**, abra o **Prompt de Comando do Desenvolvedor para VS2012**.  
  
2.  Altere para o subdiretório Arquivos de Programas\Microsoft Visual Studio *Versão*\Common7\Tools ou Arquivos de Programas (x86)\Microsoft Visual Studio *Versão*\Common7\Tools da sua instalação.  
  
3.  Execute VSVARS32.bat digitando **VSVARS32**.  
  
    > [!CAUTION]
    >  VSVARS32.bat pode variar de um computador para outro. Não substitua um arquivo VSVARS32.bat não encontrado ou danificado com um VSVARS32.bat de outro computador. Em vez disso, execute novamente a instalação para substituir o arquivo não encontrado.  
  
## <a name="see-also"></a>Consulte também  
 [Build pela linha de comando com csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)
