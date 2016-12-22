---
title: "Como fornecer uma caixa de di&#225;logo de progresso para opera&#231;&#245;es de arquivo (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "caixa de diálogo de progresso [C#]"
ms.assetid: 01b71fe7-8178-4dc8-aeb1-12053be7b51c
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como fornecer uma caixa de di&#225;logo de progresso para opera&#231;&#245;es de arquivo (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

É possível fornecer uma caixa de diálogo padrão que mostra o andamento em operações de arquivo no Windows se você usa o método <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> no namespace de <xref:Microsoft.VisualBasic?displayProperty=fullName>.  
  
 [!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### Para adicionar uma referência em Visual Studio  
  
1.  Na barra de menus, escolha **Projeto**, **Adicionar Referência**.  
  
     A caixa de diálogo **Gerenciador de Referências** aparece.  
  
2.  Na área **Assemblies**, escolha **Framework**, se ainda não estiver selecionado.  
  
3.  Na lista de nomes, selecione a caixa de seleção **Microsoft.VisualBasic** e clique no botão **OK** para fechar a caixa de diálogo.  
  
## Exemplo  
 O código a seguir copia o diretório que o `sourcePath` especifica para o diretório especificado por `destinationPath`.  Esse código também oferece uma caixa de diálogo padrão que mostra o tempo estimado restante antes da conclusão da operação.  
  
 [!code-cs[csFilesandFolders#11](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-provide-a-progress-dialog-box-for-file-operations_1.cs)]  
  
## Consulte também  
 [Sistema de arquivos e o Registro](../../../csharp/programming-guide/file-system/file-system-and-the-registry.md)