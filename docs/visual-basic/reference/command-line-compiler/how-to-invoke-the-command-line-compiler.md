---
title: Como invocar o compilador de linha de comando (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- command-line arguments
- vbc.exe
- Visual Basic compiler, starting
- command line [Visual Basic], arguments
ms.assetid: 0fd9a8f6-f34e-4c35-a49d-9b9bbd8da4a9
caps.latest.revision: 28
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 20239045426e466ba58427bb9794ea7e55b3aa4c
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-invoke-the-command-line-compiler-visual-basic"></a>Como invocar o compilador de linha de comando (Visual Basic)
Você pode chamar o compilador de linha de comando digitando o nome do seu arquivo executável na linha de comando, também conhecido como o prompt do MS-DOS. Se você compilar a partir do Prompt de comando padrão, você deve digitar o caminho totalmente qualificado para o arquivo executável. Para substituir esse comportamento padrão, você pode usar o Prompt de comando do Visual Studio, ou modificar a variável de ambiente PATH. Permitem que você compile a partir de qualquer diretório simplesmente digitando o nome do compilador.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-invoke-the-compiler-using-the-visual-studio-command-prompt"></a>Para chamar o compilador utilizando o Prompt de comando do Visual Studio  
  
1.  Abra a pasta de programa ferramentas do Visual Studio no grupo de programas do Microsoft Visual Studio.  
  
2.  Você pode usar o Prompt de comando do Visual Studio para acessar o compilador de qualquer diretório em seu computador, se o Visual Studio está instalado.  
  
3.  Invoque o Prompt de comando do Visual Studio.  
  
4.  Na linha de comando, digite `vbc.exe` *sourceFileName* e pressione ENTER.  
  
     Por exemplo, se você armazenou seu código-fonte em um diretório chamado `SourceFiles`, abra o Prompt de comando e o tipo `cd SourceFiles` para alterar a esse diretório. Se o diretório contiver um arquivo de origem chamado `Source.vb`, você pode compilá-lo digitando `vbc.exe Source.vb`.  
  
### <a name="to-set-the-path-environment-variable-to-the-compiler-for-the-windows-command-prompt"></a>Para definir a variável de ambiente PATH para o compilador para o Prompt de comando do Windows  
  
1.  Use o recurso de pesquisa do Windows para localizar Vbc.exe em seu disco local.  
  
     O nome exato da pasta onde está o compilador depende do local do diretório do Windows e a versão do ".NET Framework" instalado. Se você tiver mais de uma versão de ".NET Framework" instalado, você deve determinar qual versão usar (geralmente a versão mais recente).  
  
2.  De seu **iniciar** Menu, clique com botão direito **meu computador**e, em seguida, clique em **propriedades** no menu de atalho.  
  
3.  Clique o **avançado** guia e, em seguida, clique em **variáveis de ambiente**.  
  
4.  No **sistema** painel variáveis, selecione **caminho** na lista e clique em **editar**.  
  
5.  No **sistema editar** caixa de diálogo variável, mover o ponto de inserção para o fim da cadeia de caracteres a **valor da variável** campo e digite um ponto e vírgula (;) seguido pelo nome do diretório completo encontrado na etapa 1.  
  
6.  Clique em **Okey** para confirmar suas alterações e fechar as caixas de diálogo.  
  
     Depois de alterar a variável de ambiente PATH, você pode executar o compilador do Visual Basic no Prompt de comando do Windows de qualquer diretório no computador.  
  
### <a name="to-invoke-the-compiler-using-the-windows-command-prompt"></a>Para chamar o compilador usando o Prompt de comando do Windows  
  
1.  Do **iniciar** menu, clique no **Acessórios** pasta e, em seguida, abra o **Prompt de comando do Windows**.  
  
2.  Na linha de comando, digite `vbc.exe` *sourceFileName* e pressione ENTER.  
  
     Por exemplo, se você armazenou seu código-fonte em um diretório chamado `SourceFiles`, abra o Prompt de comando e o tipo `cd SourceFiles` para alterar a esse diretório. Se o diretório contiver um arquivo de origem chamado `Source.vb`, você pode compilá-lo digitando `vbc.exe Source.vb`.  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Compilação Condicional](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
