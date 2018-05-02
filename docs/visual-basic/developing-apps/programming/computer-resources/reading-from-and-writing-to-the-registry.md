---
title: Lendo e gravando a partir do Registro (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- My.Computer.Registry object, tasks
- registry [Visual Basic], writing to
- registry [Visual Basic], reading
ms.assetid: a13da106-185b-41d7-b23c-416da65e21e4
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a207b169e267fbcaccd46f7240d81afb3db27a8c
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="reading-from-and-writing-to-the-registry-visual-basic"></a>Lendo e gravando a partir do Registro (Visual Basic)
Este tópico descreve as tarefas e tópicos conceituais associados ao Registro.  
  
 Ao programar em Visual Basic, você pode optar por acessar o Registro por meio das funções fornecidas pelo Visual Basic ou das classes de Registro do .NET Framework. O Registro hospeda informações do sistema operacional, bem como informações de aplicativos hospedados no computador. Trabalhar com o Registro pode comprometer a segurança ao permitir o acesso inadequado aos recursos do sistema ou a informações protegidas.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Como Criar uma Chave do Registro e Definir o Valor](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-create-a-registry-key-and-set-its-value.md)  
 Descreve como usar os métodos `CreateSubKey` e `SetValue` do objeto `My.Computer.Registry` para criar uma chave do Registro e definir seu valor.  
  
 [Como Ler um Valor de uma Chave do Registro](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-read-a-value-from-a-registry-key.md)  
 Descreve como usar o método `GetValue` do objeto `My.Computer.Registry` para ler um valor de uma chave do Registro.  
  
 [Como Excluir uma Chave do Registro](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-delete-a-registry-key.md)  
 Descreve como usar o método `DeleteSubKey` da propriedade `My.Computer.Registry.CurrentUser` para excluir uma chave do Registro.  
  
 [Lendo e Gravando no Registro Usando o Namespace Microsoft.Win32](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry-using-the-microsoft-win32-namespace.md)  
 Descreve como usar as classes `Registry` e `RegistryKey` do [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] para acessar o Registro.  
  
 [Segurança e Registro](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)  
 Aborda questões de segurança que envolvem o Registro.  
  
## <a name="related-sections"></a>Seções relacionadas  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>  
 Lista e explica membros do objeto `My.Computer.Registry`.  
  
 <xref:Microsoft.Win32.Registry>  
 Apresenta uma visão geral da classe `Registry`, bem como links para membros e chaves individuais.
