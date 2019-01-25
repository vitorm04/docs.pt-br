---
title: 'Como: Invocar o compilador de linha de comando (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments
- vbc.exe
- Visual Basic compiler, starting
- command line [Visual Basic], arguments
ms.assetid: 0fd9a8f6-f34e-4c35-a49d-9b9bbd8da4a9
ms.openlocfilehash: dd5fadb9c9f248b5fb4f289bb2d24f1b085a79a8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54503723"
---
# <a name="how-to-invoke-the-command-line-compiler-visual-basic"></a>Como: Invocar o compilador de linha de comando (Visual Basic)
Você pode invocar o compilador de linha de comando, digitando o nome do seu arquivo executável na linha de comando, também conhecido como prompt do MS-DOS. Se você compilar do Prompt de comando do Windows padrão, você deve digitar o caminho totalmente qualificado para o arquivo executável. Para substituir esse comportamento padrão, você pode usar o Prompt de comando do desenvolvedor para Visual Studio ou modificar a variável de ambiente PATH. Ambos permitem que você compile de qualquer diretório simplesmente digitando o nome do compilador.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-invoke-the-compiler-using-the-developer-command-prompt-for-visual-studio"></a>Para chamar o compilador usando o Prompt de comando do desenvolvedor para Visual Studio  
  
1.  Abra a pasta do programa de ferramentas do Visual Studio dentro do grupo de programas do Microsoft Visual Studio.  
  
2.  Você pode usar o Prompt de comando do desenvolvedor para Visual Studio para acessar o compilador a partir de qualquer diretório em seu computador, se o Visual Studio está instalado.  
  
3.  Invocar o Prompt de comando do desenvolvedor para Visual Studio.  
  
4.  Na linha de comando, digite `vbc.exe` *sourceFileName* e, em seguida, pressione ENTER.  
  
     Por exemplo, se você armazenou seu código-fonte em um diretório chamado `SourceFiles`, abra o Prompt de comando e o tipo `cd SourceFiles` para alterar para aquele diretório. Se o diretório contiver um arquivo de origem denominado `Source.vb`, você pode compilá-lo digitando `vbc.exe Source.vb`.  
  
### <a name="to-set-the-path-environment-variable-to-the-compiler-for-the-windows-command-prompt"></a>Para definir a variável de ambiente PATH para o compilador para o Prompt de comando do Windows  
  
1.  Use o recurso do Windows Search para encontrar Vbc.exe em seu disco local.  
  
     O nome exato da pasta onde está o compilador depende do local do diretório do Windows e a versão do ".NET Framework" instalado. Se você tiver mais de uma versão do ".NET Framework" instalado, você deve determinar qual versão usar (geralmente a versão mais recente).  
  
2.  De seu **inicie** Menu, clique com botão direito **meu computador**e, em seguida, clique em **propriedades** no menu de atalho.  
  
3.  Clique o **Advanced** guia e, em seguida, clique em **variáveis de ambiente**.  
  
4.  No **System** painel de variáveis, selecione **caminho** na lista e clique em **editar**.  
  
5.  No **Editar System** caixa de diálogo variável, mover o ponto de inserção para o fim da cadeia de caracteres a **valor da variável** do campo e digite um ponto e vírgula (;) seguido pelo nome do diretório completo encontrado na etapa 1.  
  
6.  Clique em **Okey** para confirmar as edições e fechar as caixas de diálogo.  
  
     Depois de alterar a variável de ambiente PATH, você pode executar o compilador do Visual Basic no Prompt de comando do Windows de qualquer diretório no computador.  
  
### <a name="to-invoke-the-compiler-using-the-windows-command-prompt"></a>Para chamar o compilador usando o Prompt de comando do Windows  
  
1.  Dos **iniciar** menu, clique na **Acessórios** pasta e, em seguida, abra o **Prompt de comando do Windows**.  
  
2.  Na linha de comando, digite `vbc.exe` *sourceFileName* e, em seguida, pressione ENTER.  
  
     Por exemplo, se você armazenou seu código-fonte em um diretório chamado `SourceFiles`, abra o Prompt de comando e o tipo `cd SourceFiles` para alterar para aquele diretório. Se o diretório contiver um arquivo de origem denominado `Source.vb`, você pode compilá-lo digitando `vbc.exe Source.vb`.  
  
## <a name="see-also"></a>Consulte também
- [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Compilação Condicional](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
