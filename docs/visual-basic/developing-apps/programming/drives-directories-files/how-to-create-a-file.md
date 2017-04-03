---
title: Como Criar um Arquivo no Visual Basic | Microsoft Docs
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- text files, creating
- files, creating
ms.assetid: 0253bb6d-5519-4a50-b882-b93ef5cca0d9
caps.latest.revision: 15
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 87d0487ab2bb953fcde1de884d1cbed1fe592c36
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-create-a-file-in-visual-basic"></a>Como criar um arquivo no Visual Basic
Este exemplo cria um arquivo de texto vazio no caminho especificado usando o método <xref:System.IO.File.Create%2A> na classe <xref:System.IO.File>.  
  
## <a name="example"></a>Exemplo  
 [!code-vb[VbFileIOMisc#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-file_1.vb)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Use a variável `file` para gravar no arquivo.  
  
## <a name="robust-programming"></a>Programação robusta  
 Se o arquivo já existir, ele será substituído.  
  
 As seguintes condições podem causar uma exceção:  
  
-   O nome do caminho está malformado. Por exemplo, ele contém caracteres inválidos ou é somente um espaço em branco (<xref:System.ArgumentException>).  
  
-   O caminho é somente leitura (<xref:System.IO.IOException>).  
  
-   O nome do caminho é `Nothing` (<xref:System.ArgumentNullException>).  
  
-   O nome do caminho é muito longo (<xref:System.IO.PathTooLongException>).  
  
-   O caminho é inválido (<xref:System.IO.DirectoryNotFoundException>).  
  
-   O caminho é apenas dois-pontos ":" (<xref:System.NotSupportedException>).  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Uma <xref:System.Security.SecurityException> poderá ser lançada em ambientes de confiança parcial.  
  
 A chamada para o método <xref:System.IO.File.Create%2A> requer <xref:System.Security.Permissions.FileIOPermission>.  
  
 Uma <xref:System.UnauthorizedAccessException> será lançada se o usuário não tiver permissão para criar o arquivo.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.IO>   
 <xref:System.IO.File.Create%2A>   
 [Usando Bibliotecas de Código Parcialmente Confiável](http://msdn.microsoft.com/library/dd66cd4c-b087-415f-9c3e-94e3a1835f74)   
 [Noções Básicas da Segurança de Acesso do Código](https://msdn.microsoft.com/library/33tceax8)
