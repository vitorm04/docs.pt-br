---
title: "/reference (C# Compiler Options) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/reference"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/r compiler option [C#]"
  - "reference compiler option [C#]"
  - "r compiler option [C#]"
  - "/reference compiler option [C#]"
  - "-r compiler option [C#]"
  - "metadata import [C#]"
  - "public type information [C#]"
  - "-reference compiler option [C#]"
ms.assetid: 8d13e5b0-abf6-4c46-bf71-2daf2cd0a6c4
caps.latest.revision: 28
caps.handback.revision: 28
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /reference (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A opção de **\/reference** faz com que o compilador importar informações de tipo de [público](../../../csharp/language-reference/keywords/public.md) no arquivo especificado no projeto atual, permitindo que você o para referenciar metadados dos arquivos especificados no assembly.  
  
## Sintaxe  
  
```  
/reference:[alias=]filename  
/reference:filename  
```  
  
## Arguments  
 `filename`  
 O nome de um arquivo que contém um manifesto do assembly.  Para importar mais de um arquivo, incluindo uma opção de **\/reference** separada para cada arquivo.  
  
 `alias`  
 Um identificador válido do C\# que representa um namespace raiz que contém todos os namespaces no assembly.  
  
## Comentários  
 Para importar de mais de um arquivo, incluindo uma opção de **\/reference** para cada arquivo.  
  
 Os arquivos que você importa devem conter um manifesto; o arquivo de saída deve ter sido criado com uma das opções de [\/target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) diferentes de [\/target: módulo](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md).  
  
 **\/r** é a forma abreviada de **\/reference**.  
  
 Use [\/addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md) para importar metadados de um arquivo de saída que não contém um manifesto do assembly.  
  
 Se você referenciar o assembly um assembly \(A\) que faz referência a outro assembly assembly \(B\), você precisará fazer referência ao assembly B se:  
  
-   Um tipo que você usa de assembly A herda de um tipo ou implementa uma interface do assembly B.  
  
-   Você invoca um campo, uma propriedade, um evento, ou um método que tem um tipo de retorno ou um tipo de parâmetro do assembly B.  
  
 Use [\/lib](../../../csharp/language-reference/compiler-options/lib-compiler-option.md) para especificar o diretório no qual uma ou mais de suas referências de assembly é encontrado.  O tópico de **\/lib** também discute os diretórios na qual o compilador pesquisa assemblies.  
  
 Para que o compilador reconheça um tipo em um assembly, e não em um módulo, precisa ser forçado para resolver o tipo, que você pode fazer definindo uma instância do tipo.  Há outras maneiras de resolver nomes de tipo em um assembly para o compilador: por exemplo, se você herda de um tipo em um assembly, o nome do tipo serão reconhecidos em seguida pelo compilador.  
  
 Às vezes é necessário fazer referência a duas versões diferentes do mesmo componente de em um assembly.  Para fazer isso, use o suboption do alias na opção de **\/reference** para cada arquivo distingue entre os dois arquivos.  Esses aliases são usadas como um qualificador para o nome do componente, e serão resolvidas para o componente em um dos arquivos.  
  
 O arquivo de resposta de .rsp csc \(\), que faz referência aos assemblies comumente do .NET Framework, é usado por padrão.  Use [\/noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) se você não quiser que o compilador para usar csc.rsp.  
  
> [!NOTE]
>  No Visual Studio, use a caixa de diálogo de **Adicionar Referência** .  Para obter mais informações, consulte [Como adicionar ou remover referências usando a caixa de diálogo Adicionar Referência](http://msdn.microsoft.com/pt-br/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  No Visual Studio 2010 e em versões posteriores, para assegurar o comportamento equivalente entre adicionar referências usando `/reference` e usando a caixa de diálogo **Adicionar Referência** , a propriedade de **Inserir Tipos Interop** deve ser definida como **False** para o assembly que está sendo adicionado.  **True** é o valor padrão para essa propriedade.  
  
## Exemplo  
 Este exemplo mostra como usar o recurso de [alias extern](../../../csharp/language-reference/keywords/extern-alias.md) .  
  
 Você cria os metadados do arquivo de origem e de importação de `grid.dll` e de `grid20.dll`,que já foram criados anteriormente.  Os dois DLL contêm versões separadas do mesmo componente, e você usa dois **\/reference** com opções de alias criar o arquivo de origem.  As opções são semelhantes a esta:  
  
 \/reference:GridV1\=grid.dll e \/reference:GridV2\=grid20.dll  
  
 Isso configura de alias externos “GridV1” e “GridV2”, que você usa em seu programa por meio de uma instrução extern:  
  
```  
extern alias GridV1;  
extern alias GridV2;  
// Using statements go here.  
```  
  
 Uma vez que isso é feito, você pode consultar o controle de grade de grid.dll prefixando o nome do controle com o GridV1, como este:  
  
```  
GridV1::Grid  
```  
  
 Além disso, você pode consultar o controle de grade de grid20.dll prefixando o nome do controle com o GridV2 como este:  
  
```  
GridV2::Grid   
```  
  
## Consulte também  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [Como modificar as propriedades de projeto e as definições de configuração](http://msdn.microsoft.com/pt-br/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)