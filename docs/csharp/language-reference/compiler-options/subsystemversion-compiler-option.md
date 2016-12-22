---
title: "-subsystemversion (op&#231;&#245;es do compilador c#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
ms.assetid: a99fce81-9d92-4813-9874-bee777041445
caps.latest.revision: 19
caps.handback.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /subsystemversion (op&#231;&#245;es do compilador C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Especifica a versão mínima do subsistema no qual pode executar o arquivo executável gerado, assim, determinar as versões do Windows no qual o arquivo executável pode executar. Normalmente, essa opção garante que o arquivo executável pode aproveitar os recursos de segurança em especial que não estão disponíveis com versões anteriores do Windows.  
  
> [!NOTE]
>  Para especificar o próprio subsistema, use o [/destino](../../../csharp/language-reference/compiler-options/target-compiler-option.md) opção de compilador.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
/subsystemversion:major.minor  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `major.minor`  
 A versão mínima necessária do subsistema, conforme expresso em uma notação de ponto para versões principais e secundárias. Por exemplo, você pode especificar que um aplicativo não pode ser executado em um sistema operacional que é mais antigo que o Windows 7 se você definir o valor dessa opção como 6.01, conforme descrito na tabela mais adiante neste tópico. Você deve especificar os valores de `major` e `minor` como inteiros.  
  
 Zeros à esquerda `minor` versão não altera a versão, mas fazer zeros à direita. Por exemplo, 6.1 e 6.01 referem-se a mesma versão, mas 6.10 refere-se a uma versão diferente. É recomendável expressar a versão secundária como dois dígitos para evitar confusão.  
  
## <a name="remarks"></a>Comentários  
 A seguinte tabela lista as versões do subsistema comuns do Windows.  
  
|Versão do Windows|Versão do subsistema|  
|---------------------|-----------------------|  
|Windows 2000|5.00|  
|Windows XP|5.01|  
|Windows Server 2003|5.02|  
|Windows Vista|6.00|  
|Windows 7|6.01|  
|Windows Server 2008|6.01|  
|[!INCLUDE[win8](../../../csharp/language-reference/compiler-options/includes/win8_md.md)]|6.02|  
  
## <a name="default-values"></a>Valores padrão  
 O valor padrão de **/subsystemversion** opção de compilador depende das condições na lista a seguir:  
  
-   O valor padrão é 6.02 se qualquer opção de compilador na lista a seguir é definida:  
  
    -   [/target: appcontainerexe](../../../csharp/language-reference/compiler-options/target-appcontainerexe-compiler-option.md)  
  
    -   [/target: winmdobj](../../../csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md)  
  
    -   [/Platform:ARM](../../../csharp/language-reference/compiler-options/platform-compiler-option.md)  
  
-   O valor padrão é 6.00 se você estiver usando o MSBuild, você deseja [!INCLUDE[net_v45](../../../csharp/language-reference/compiler-options/includes/net_v45_md.md)], e você não definir qualquer uma das opções de compilador que foram especificadas anteriormente na lista.  
  
-   O valor padrão é 4.00 se nenhuma das condições anteriores for true.  
  
## <a name="setting-this-option"></a>Definindo esta opção  
 Para definir o **/subsystemversion** opção de compilador no Visual Studio, abra o arquivo. csproj e especifique um valor para o `SubsystemVersion` propriedade no XML MSBuild. Você não pode definir essa opção no IDE do Visual Studio. Para obter mais informações, consulte "Valores padrão" anteriormente neste tópico ou [Propriedades comuns de projeto MSBuild](/visual-studio/msbuild/common-msbuild-project-properties).  
  
## <a name="see-also"></a>Consulte também  
 [Opções do compilador c#](../../../csharp/language-reference/compiler-options/index.md)