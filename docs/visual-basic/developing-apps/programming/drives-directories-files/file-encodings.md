---
title: "Codifica&#231;&#245;es de arquivo (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
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
  - "codificações de caracteres"
  - "codificação de arquivos"
  - "Arquivos , codificação"
  - "Unicode, codificação de arquivos"
ms.assetid: ea2c5f5f-bbb1-4150-9928-b9951fa6bc57
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Codifica&#231;&#245;es de arquivo (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Codificações de arquivo, também conhecido como codificações de caracteres, especificam como deseja representar caracteres quando estiver processando um texto.  Uma codificação pode ser preferível sobre outra em termos de quais caracteres de idioma ela pode ou não tratar, embora Unicode seja geralmente preferido.  
  
 Quando lendo de ou gravando em aos arquivos, correspondências de modo inadequado de codificações de arquivo podem resultar em exceções ou resultados incorretos.  
  
## Tipos de Codificações  
 Unicode é a codificação preferencial ao trabalhar com arquivos.  Unicode é um padrão mundial de codificação de caracteres que usa valores de código de 16 bits para representar todos os caracteres usados na computação moderna, incluindo símbolos técnicos e caracteres especiais usados em editoração.  
  
 Padrões de codificação de caracteres anteriores consistiam de conjuntos de caracteres tradicionais, como o conjunto de caracteres Windows ANSI que usa valores de código de 8 bits, ou combinações de valores de 8 bits, para representar os caracteres usados em um idioma específico ou região geográfica.  
  
## Classe Encoding  
 A classe <xref:System.Text.Encoding> representa uma codificação de caracteres.  Esta tabela lista os tipos de codificações disponíveis e descreve cada um.  
  
|||  
|-|-|  
|Nome|Descrição|  
|<xref:System.Text.ASCIIEncoding>|Representa uma codificação de caracteres ASCII de caracteres Unicode.|  
|<xref:System.Text.UnicodeEncoding>|Representa uma codificação UTF\-16 de caracteres Unicode.|  
|<xref:System.Text.UTF32Encoding>|Representa uma codificação UTF\-32 de caracteres Unicode.|  
|<xref:System.Text.UTF7Encoding>|Representa uma codificação UTF\-7 de caracteres Unicode.|  
|<xref:System.Text.UTF8Encoding>|Representa uma codificação UTF\-8 de caracteres Unicode.|  
  
## Consulte também  
 [Lendo a partir de arquivos](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)   
 [Gravando em arquivos](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)