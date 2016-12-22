---
title: "Lendo e gravando no Registro usando o namespace Microsoft.Win32 (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Registro, o Visual Basic"
ms.assetid: 4a0dcce0-c27b-4199-baa8-ee4528da6a56
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Lendo e gravando no Registro usando o namespace Microsoft.Win32 (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Embora `My.Computer.Registry` deve abranger as necessidades básicas ao programar contra o registro, você também pode usar o <xref:Microsoft.Win32.Registry> e <xref:Microsoft.Win32.RegistryKey> classes de <xref:Microsoft.Win32> namespace do [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)].  
  
## <a name="keys-in-the-registry-class"></a>Chaves na classe do registro  
 O <xref:Microsoft.Win32.Registry> classe fornece as chaves do registro base que podem ser usadas para acessar subchaves e seus valores. As chaves base são somente leitura. A tabela a seguir lista e descreve as sete chaves expostas pelo <xref:Microsoft.Win32.Registry> classe.  
  
|**Chave**|**Descrição**|  
|-------------|---------------------|  
|<xref:Microsoft.Win32.Registry.ClassesRoot>|Define os tipos de documentos e as propriedades associadas a esses tipos.|  
|<xref:Microsoft.Win32.Registry.CurrentConfig>|Contém informações de configuração de hardware que não são específicas do usuário.|  
|<xref:Microsoft.Win32.Registry.CurrentUser>|Contém informações sobre as preferências do usuário atual, como variáveis de ambiente.|  
|<xref:Microsoft.Win32.Registry.DynData>|Contém dados de registro dinâmico, como os usados por Drivers de dispositivo Virtual.|  
|<xref:Microsoft.Win32.Registry.LocalMachine>|Contém cinco subchaves (Hardware, SAM, Security, Software e sistema) que armazenam os dados de configuração para o computador local.|  
|<xref:Microsoft.Win32.Registry.PerformanceData>|Contém informações de desempenho de componentes de software.|  
|<xref:Microsoft.Win32.Registry.Users>|Contém informações sobre as preferências do usuário padrão.|  
  
> [!IMPORTANT]
>  É mais seguro gravar dados para o usuário atual (<xref:Microsoft.Win32.Registry.CurrentUser>) que o computador local (<xref:Microsoft.Win32.Registry.LocalMachine>). Uma condição que é normalmente conhecida como "ilegais" ocorrerem quando a chave que você está criando tiver sido criada por outro processo possivelmente mal-intencionado. Para evitar esse problema, use um método, como <xref:Microsoft.Win32.RegistryKey.GetValue%2A>, que retorna `Nothing` se a chave ainda não existir.  
  
## <a name="reading-a-value-from-the-registry"></a>Ler um valor do registro  
 O código a seguir mostra como ler uma cadeia de caracteres de HKEY_CURRENT_USER.  
  
 [!code-vb[VbResourceTasks#20](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/reading-from-and-writing-to-the-registry-using-the-microsoft-win32-namespace_1.vb)]  
  
 O código a seguir lê, incrementa e grava uma cadeia de caracteres em HKEY_CURRENT_USER.  
  
 [!code-vb[VbResourceTasks#21](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/reading-from-and-writing-to-the-registry-using-the-microsoft-win32-namespace_2.vb)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.SystemException>   
 <xref:System.ApplicationException>   
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>   
 [Try... Catch... Instrução Finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)   
 [Lendo e gravando no registro](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)   
 [Segurança e Registro](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)