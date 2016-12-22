---
title: "/out (C# Compiler Options) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/out"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/out compiler option [C#]"
  - "out compiler option [C#]"
  - "-out compiler option [C#]"
ms.assetid: 70d91d01-7bd2-4aea-ba8b-4e9807e9caa5
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /out (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A opção de **\/out** especifica o nome do arquivo de saída.  
  
## Sintaxe  
  
```  
/out:filename  
```  
  
## Arguments  
 `filename`  
 O nome do arquivo de saída criado pelo compilador.  
  
## Comentários  
 Na linha de comando, é possível especificar vários arquivos de saída para sua compilação.  O compilador espera encontrar um ou mais arquivos de origem que seguem a opção de **\/out** .  Em seguida, qualquer arquivo de origem serão criados no arquivo de saída especificado pela opção de **\/out** .  
  
 Especifique o nome completo e a extensão do arquivo que você deseja criar.  
  
 Se você não especificar o nome do arquivo de saída:  
  
-   Um .exe terá o nome do arquivo de origem que contém o método de **Principal** .  
  
-   Um .dll ou um .netmodule tomarão o nome do primeiro arquivo de código\-fonte.  
  
 Um arquivo de código\-fonte usado para criar um arquivo de saída não pode ser usado na compilação da compilação de outro arquivo de saída.  
  
 Ao gerar vários arquivos de saída em uma compilação da linha de comando, lembre\-se de que apenas um dos arquivos de saída pode ser um assembly e somente o primeiro arquivo de saída especificado \(implicitamente ou explicitamente com **\/out**\) pode ser o assembly.  
  
 Todos os módulos gerados como parte de uma compilação se tornam arquivos associados com qualquer assembly também gerado na compilação.  Use [ildasm.exe](../Topic/Ildasm.exe%20\(IL%20Disassembler\).md) para exibir o manifesto do assembly para ver os arquivos associados.  
  
 A opção do compilador de \/out é necessária para que o exe é o destino de um assembly de amigo.  Para obter mais informações, consulte [Assemblies amigáveis](../Topic/Friend%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md).  
  
### Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio  
  
1.  Abra a página de **Propriedades** do projeto.  
  
2.  Clique na página de propriedades de **Aplicativo** .  
  
3.  Modifique a propriedade de **Nome do Assembly** .  
  
     Para definir programaticamente essa opção do compilador: <xref:VSLangProj80.ProjectProperties3.OutputFileName%2A> é uma propriedade somente leitura, que é determinada por uma combinação de tipo de projeto \(exe, biblioteca, e assim por diante\) e o nome do assembly.  Alterar uma ou ambas as propriedade será necessária para definir o nome do arquivo de saída.  
  
## Exemplo  
 Criar `t.cs` e crie o arquivo de saída `t.exe`, bem como criar `t2.cs` e crie o arquivo de saída `mymodule.netmodule`de módulo:  
  
```  
csc t.cs /out:mymodule.netmodule /target:module t2.cs  
```  
  
## Consulte também  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [Assemblies amigáveis](../Topic/Friend%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md)   
 [Como modificar as propriedades de projeto e as definições de configuração](http://msdn.microsoft.com/pt-br/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)