---
title: "/reference (Visual Basic) | Microsoft Docs"
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
  - "Opção de compilador /r [Visual Basic]"
  - "Opção de compilador /reference [Visual Basic]"
  - "Opção de compilador r [Visual Basic]"
  - "Opção de compilador -r [Visual Basic]"
  - "Opção de compilador reference [Visual Basic]"
  - "Opção de compilador -reference [Visual Basic]"
ms.assetid: 66bdfced-bbf6-43d1-a554-bc0990315737
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /reference (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Faz com que o compilador torne informações de tipo nas montagens especificadas disponíveis para o projeto que você está compilando atualmente.  
  
## Sintaxe  
  
```  
/reference:fileList  
' -or-  
/r:fileList  
```  
  
## Argumentos  
  
|||  
|-|-|  
|Termo|Definição|  
|`fileList`|Obrigatório.  Lista separada por vírgulas de nomes de arquivo da montagem.  Se o nome do arquivo contiver um espaço, envolva\-o com aspas  \(""\).|  
  
## Comentários  
 O\(s\) arquivo\(s\) que você importar devem conter metadados do assembly.  Apenas tipos públicos são visíveis fora do assembly.  A opção [\/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) importa os metadados de um módulo.  
  
 Se você referencia um conjunto de módulos \(Assembly A\)  que se faz referência a outro conjunto de módulos \(assembly B\), você precisa referenciar o Assembly B se:  
  
-   Um tipo do Assembly A herda de um tipo ou implementa uma interface do Assembly B.  
  
-   Um campo, propriedade, evento ou método que possui um tipo de retorno ou tipo de parâmetro de Assembly B é chamado.  
  
 Use [\/libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) para especificar o diretório no qual uma ou mais das suas referências do assembly estão localizadas.  
  
 Para o compilador reconhecer um tipo em um conjunto de módulos \(não um módulo\), ele deve ser forçado a decidir o tipo.  Um exemplo de como você pode fazer isso é definir uma instância do tipo.  Outras maneiras estão disponíveis para decidir nomes de tipo em um conjunto de módulos \(assembly\) para o compilador.  Por exemplo, se você herdar de um tipo em um conjunto de módulos \(assembly\), o nome do tipo, em seguida, torna\-se conhecido para o compilador.  
  
 O arquivo de resposta Vbc.rsp, que referencia conjuntos de módulos \(assemblies\) [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] muito usados, é usado por padrão.  Use `/noconfig` se você não quiser que o compilador use o Vbc.rsp.  
  
 A forma curta de `/reference`  é `/r`.  
  
## Exemplo  
 O código a seguir compila o arquivo fonte `nput.vb` e referencia conjuntos de módulos \(assemblies\) de M`etad1.dll` e M `etad2.dll` para produzir O `ut.exe`.  
  
```  
vbc /reference:metad1.dll,metad2.dll /out:out.exe input.vb  
```  
  
## Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)   
 [\/target](../../../visual-basic/reference/command-line-compiler/target.md)   
 [Público](../../../visual-basic/language-reference/modifiers/public.md)   
 [Linhas de comando de compilação de exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)