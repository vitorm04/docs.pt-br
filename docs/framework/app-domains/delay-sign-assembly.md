---
title: Atrasando a assinatura de um assembly
ms.date: 07/31/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- deferring assembly signing
- signing assemblies
- assemblies [.NET Framework], signing
- strong-named assemblies, delaying assembly signing
- partial assembly signing
ms.assetid: 9d300e17-5bf1-4360-97da-2aa55efd9070
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eb055285af7365536f7e1ad7c7d9290e51be50db
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66832864"
---
# <a name="delay-signing-an-assembly"></a>Atrasando a assinatura de um assembly
Uma organização pode ter um par de chaves bem protegido ao qual os desenvolvedores não têm acesso todos os dias. A chave pública normalmente está disponível, mas o acesso à chave privada é restrito a apenas algumas pessoas. Ao desenvolver assemblies com nomes fortes, cada assembly que referencia o assembly de destino com nome forte contém o token da chave pública usada para fornecer ao assembly de destino um nome forte. Isso requer que a chave pública esteja disponível durante o processo de desenvolvimento.  
  
 Você pode usar a assinatura atrasada ou parcial no tempo de build para reservar espaço no arquivo PE para a assinatura de nome forte, mas atrasar a assinatura de fato até um estágio posterior (normalmente imediatamente antes de enviar o assembly).  
  
 As etapas a seguir descrevem o processo de atrasar a assinatura de um assembly:  
  
1. Obtenha a parte da chave pública do par de chaves da organização que fará a eventual assinatura. Normalmente, essa chave está na forma de um arquivo .snk, que pode ser criado usando a [ferramenta Nome Forte (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) fornecida pelo SDK (Software Development Kit) do Windows.  
  
2. Anote o código-fonte para o assembly com dois atributos personalizados de <xref:System.Reflection>:  
  
    - <xref:System.Reflection.AssemblyKeyFileAttribute>, que passa o nome do arquivo que contém a chave pública como um parâmetro para seu construtor.  
  
    - <xref:System.Reflection.AssemblyDelaySignAttribute>, que indica que esse atraso na assinatura está sendo usado passando **true** como um parâmetro para seu construtor. Por exemplo:  
  
         [!code-cpp[AssemblyDelaySignAttribute#4](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cpp/source2.cpp#4)]
         [!code-csharp[AssemblyDelaySignAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cs/source2.cs#4)]
         [!code-vb[AssemblyDelaySignAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyDelaySignAttribute/vb/source2.vb#4)]  
  
3. O compilador insere a chave pública no manifesto do assembly e reserva espaço no arquivo PE para a assinatura de nome forte completo. A chave pública real deve ser armazenada enquanto o assembly é compilado para que outros assemblies que referenciam esse assembly possam obter a chave para armazenar em sua própria referência do assembly.  
  
4. Como o assembly não tem uma assinatura de nome forte válida, a verificação dessa assinatura deve ser desativada. Você pode fazer isso usando a opção **– Vr** com a ferramenta Nome Forte.  
  
     O exemplo a seguir desativa a verificação para um assembly chamado `myAssembly.dll`.  
  
    ```  
    sn –Vr myAssembly.dll  
    ```  
  
     Para desligar a verificação em plataformas em que você não pode executar a ferramenta Nome Forte, como microprocessadores ARM (Advanced RISC Machine), use a opção **–Vk** para criar um arquivo de Registro. Importe o arquivo de Registro para o Registro no computador em que você deseja desligar a verificação. O exemplo a seguir cria um arquivo de Registro para `myAssembly.dll`.  
  
    ```  
    sn –Vk myRegFile.reg myAssembly.dll  
    ```  
  
     Com a opção **–Vr** ou a **–Vk**, você pode, opcionalmente, incluir um arquivo .snk para a assinatura da chave de teste.  
  
    > [!WARNING]
    > Por segurança, não confie em nomes fortes. Eles apenas fornecem uma identidade exclusiva.
  
    > [!NOTE]
    >  Se você usar o atraso de assinatura durante o desenvolvimento com o Visual Studio em um computador de 64 bits e compilar um assembly para **Qualquer CPU**, talvez seja necessário aplicar a opção **-Vr** duas vezes. (No Visual Studio, **Qualquer CPU** é um valor da propriedade de build **Destino de Plataforma**, quando você compila da linha de comando, esse é o padrão.) Para executar seu aplicativo da linha de comando ou do Explorador de Arquivos, use a versão de 64 bits do [Sn.exe (ferramenta Nome Forte)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) para aplicar a opção **-Vr** ao assembly. Para carregar o assembly no Visual Studio no tempo de design (por exemplo, se o assembly contiver componentes que são usados por outros assemblies em seu aplicativo), use a versão de 32 bits da ferramenta de nome forte. Isso ocorre porque o compilador JIT (Just-in-time) compila o assembly para código nativo de 64 bits quando o assembly é executado da linha de comando e para código nativo de 32 bits quando o assembly é carregado no ambiente de tempo de design.  
  
5. Posteriormente, normalmente imediatamente antes do envio, você envia o assembly para a autoridade de assinatura da sua organização para a assinatura de nome forte real usando a opção **–R** com a ferramenta Nome Forte.  
  
     O exemplo a seguir assina um assembly chamado `myAssembly.dll` com um nome forte usando o par de chaves `sgKey.snk`.  
  
    ```  
    sn -R myAssembly.dll sgKey.snk  
    ```  
  
## <a name="see-also"></a>Consulte também

- [Criação de assemblies](../../../docs/framework/app-domains/create-assemblies.md)
- [Como: criar um par de chaves pública/privada](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)
- [Sn.exe (Ferramenta Nome Forte)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)
- [Programação com assemblies](../../../docs/framework/app-domains/programming-with-assemblies.md)
