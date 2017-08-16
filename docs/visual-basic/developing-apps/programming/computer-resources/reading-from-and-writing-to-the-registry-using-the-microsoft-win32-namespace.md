---
title: Lendo e gravando no Registro usando o namespace Microsoft.Win32 (Visual Basic)
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
- registry, Visual Basic
ms.assetid: 4a0dcce0-c27b-4199-baa8-ee4528da6a56
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: cefde5317b2ed2bc0a2834224b1475e8020f7f25
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="reading-from-and-writing-to-the-registry-using-the-microsoftwin32-namespace-visual-basic"></a>Lendo e gravando no Registro usando o namespace Microsoft.Win32 (Visual Basic)
`My.Computer.Registry` deve suprir suas necessidades básicas ao programar no registro, mas você também pode usar as classes <xref:Microsoft.Win32.Registry> e <xref:Microsoft.Win32.RegistryKey> do namespace <xref:Microsoft.Win32> do [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].  
  
## <a name="keys-in-the-registry-class"></a>Chaves na classe de Registro  
 A classe <xref:Microsoft.Win32.Registry> fornece as chaves base do Registro que podem ser usadas para acessar subchaves e seus valores. As chaves base em si são somente leitura. A tabela a seguir lista e descreve as sete chaves expostas pela classe <xref:Microsoft.Win32.Registry>.  
  
|**Chave**|**Descrição**|  
|-------------|---------------------|  
|<xref:Microsoft.Win32.Registry.ClassesRoot>|Define os tipos de documentos e as propriedades associadas a esses tipos.|  
|<xref:Microsoft.Win32.Registry.CurrentConfig>|Contém informações de configuração de hardware que não são específicas do usuário.|  
|<xref:Microsoft.Win32.Registry.CurrentUser>|Contém informações sobre as preferências do usuário atual, como variáveis ambientais.|  
|<xref:Microsoft.Win32.Registry.DynData>|Contém dados do registro dinâmico, como aqueles usados por Drivers de dispositivo virtual.|  
|<xref:Microsoft.Win32.Registry.LocalMachine>|Contém cinco subchaves (Hardware, SAM, Segurança, Software e Sistema) que armazenam os dados de configuração do computador local.|  
|<xref:Microsoft.Win32.Registry.PerformanceData>|Contém informações de desempenho de componentes de software.|  
|<xref:Microsoft.Win32.Registry.Users>|Contém informações sobre as preferências do usuário padrão.|  
  
> [!IMPORTANT]
>  É mais seguro gravar dados na pasta do usuário atual (<xref:Microsoft.Win32.Registry.CurrentUser>) do que no computador local (<xref:Microsoft.Win32.Registry.LocalMachine>). Uma condição que costuma ser chamada de "squatting" ocorre quando a chave que você está criando foi criada anteriormente por outro processo, possivelmente mal-intencionado. Para evitar que isso ocorra, use um método, como <xref:Microsoft.Win32.RegistryKey.GetValue%2A>, que retornará `Nothing` se a chave ainda não existir.  
  
## <a name="reading-a-value-from-the-registry"></a>Lendo um valor do Registro  
 O código a seguir mostra como ler uma cadeia de caracteres de HKEY_CURRENT_USER.  
  
 [!code-vb[VbResourceTasks#20](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/reading-from-and-writing-to-the-registry-using-the-microsoft-win32-namespace_1.vb)]  
  
 O código a seguir lê, incrementa e grava uma cadeia de caracteres em HKEY_CURRENT_USER.  
  
 [!code-vb[VbResourceTasks#21](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/reading-from-and-writing-to-the-registry-using-the-microsoft-win32-namespace_2.vb)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.SystemException>   
 <xref:System.ApplicationException>   
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>   
 [Instrução Try...Catch...Finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)   
 [Lendo e Gravando do Registro](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)   
 [Segurança e Registro](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)

