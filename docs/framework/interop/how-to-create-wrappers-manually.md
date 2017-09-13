---
title: Como criar wrappers manualmente
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- wrappers, creating manually
ms.assetid: cc2a70d8-6a58-4071-a8cf-ce28c018c09b
caps.latest.revision: 8
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 218e92b379d562be66c72cb731654907766f2ec4
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="how-to-create-wrappers-manually"></a><span data-ttu-id="a5253-102">Como criar wrappers manualmente</span><span class="sxs-lookup"><span data-stu-id="a5253-102">How to: Create Wrappers Manually</span></span>
<span data-ttu-id="a5253-103">Se você decidir declarar tipos COM manualmente no código-fonte gerenciado, o melhor lugar para começar é com um arquivo de linguagem IDL ou uma biblioteca de tipos existente.</span><span class="sxs-lookup"><span data-stu-id="a5253-103">If you decide to declare COM types manually in managed source code, the best place to start is with an existing Interface Definition Language (IDL) file or type library.</span></span> <span data-ttu-id="a5253-104">Quando você não tem o arquivo IDL ou não pode gerar um arquivo de biblioteca de tipos, pode simular os tipos COM criando declarações gerenciadas e exportando o assembly resultante para uma biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="a5253-104">When you do not have the IDL file or cannot generate a type library file, you can simulate the COM types by creating managed declarations and exporting the resulting assembly to a type library.</span></span>  
  
### <a name="to-simulate-com-types-from-managed-source"></a><span data-ttu-id="a5253-105">Para simular tipos COM de uma fonte gerenciada</span><span class="sxs-lookup"><span data-stu-id="a5253-105">To simulate COM types from managed source</span></span>  
  
1.  <span data-ttu-id="a5253-106">Declare os tipos em uma linguagem que está em conformidade com o CLS (Common Language Specification) e compile o arquivo.</span><span class="sxs-lookup"><span data-stu-id="a5253-106">Declare the types in a language that is compliant with the Common Language Specification (CLS) and compile the file.</span></span>  
  
2.  <span data-ttu-id="a5253-107">Exporte o assembly que contém os tipos com o [Exportador de Biblioteca de Tipos (Tlbexp.exe)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md).</span><span class="sxs-lookup"><span data-stu-id="a5253-107">Export the assembly containing the types with the [Type Library Exporter (Tlbexp.exe)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md).</span></span>  
  
3.  <span data-ttu-id="a5253-108">Use a biblioteca de tipos COM exportada como base para declarar tipos gerenciados orientados ao COM.</span><span class="sxs-lookup"><span data-stu-id="a5253-108">Use the exported COM type library as a basis for declaring COM-oriented managed types.</span></span>  
  
### <a name="to-create-a-runtime-callable-wrapper-rcw"></a><span data-ttu-id="a5253-109">Para criar um RCW (Runtime Callable Wrapper)</span><span class="sxs-lookup"><span data-stu-id="a5253-109">To create a runtime callable wrapper (RCW)</span></span>  
  
1.  <span data-ttu-id="a5253-110">Supondo que você tenha um arquivo IDL ou um arquivo de biblioteca de tipos, decida quais classes e interfaces você deseja incluir no RCW personalizado.</span><span class="sxs-lookup"><span data-stu-id="a5253-110">Assuming that you have an IDL file or type library file, decide which classes and interfaces you want to include in the custom RCW.</span></span> <span data-ttu-id="a5253-111">Exclua todos os tipos que você não pretende usar direta ou indiretamente do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a5253-111">You can exclude any types that you do not intend to use directly or indirectly in your application.</span></span>  
  
2.  <span data-ttu-id="a5253-112">Crie um arquivo de origem em uma linguagem em conformidade com CLS e declare os tipos.</span><span class="sxs-lookup"><span data-stu-id="a5253-112">Create a source file in a CLS-compliant language and declare the types.</span></span> <span data-ttu-id="a5253-113">Consulte [Resumo da conversão de bibliotecas de tipos em assemblies](http://msdn.microsoft.com/en-us/bf3f90c5-4770-4ab8-895c-3ba1055cc958) para obter uma descrição completa do processo de conversão de importação.</span><span class="sxs-lookup"><span data-stu-id="a5253-113">See [Type Library to Assembly Conversion Summary](http://msdn.microsoft.com/en-us/bf3f90c5-4770-4ab8-895c-3ba1055cc958) for a complete description of the import conversion process.</span></span> <span data-ttu-id="a5253-114">Efetivamente, quando você cria um RCW (Runtime Callable Wrapper) personalizado, você está executando manualmente a atividade de conversão de tipo fornecida pelo [Importador da Biblioteca de Tipos (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md).</span><span class="sxs-lookup"><span data-stu-id="a5253-114">Effectively, when you create a custom RCW, you are manually performing the type conversion activity provided by the [Type Library Importer (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md).</span></span> <span data-ttu-id="a5253-115">O exemplo na próxima seção mostra os tipos em um arquivo IDL ou de biblioteca de tipos e seus tipos correspondentes no código C#.</span><span class="sxs-lookup"><span data-stu-id="a5253-115">The example in the next section shows types in an IDL or type library file and their corresponding types in C# code.</span></span>  
  
3.  <span data-ttu-id="a5253-116">Quando as declarações forem concluídas, compile o arquivo como compilaria qualquer código-fonte gerenciado.</span><span class="sxs-lookup"><span data-stu-id="a5253-116">When the declarations are complete, compile the file as you compile any other managed source code.</span></span>  
  
4.  <span data-ttu-id="a5253-117">Assim como ocorre com os tipos importados com Tlbimp.exe, alguns exigem informações adicionais, que podem ser adicionadas diretamente ao código.</span><span class="sxs-lookup"><span data-stu-id="a5253-117">As with the types imported with Tlbimp.exe, some require additional information, which you can add directly to your code.</span></span> <span data-ttu-id="a5253-118">Para obter detalhes, consulte [Como editar assemblies de interoperabilidade](http://msdn.microsoft.com/en-us/16aacb20-2269-42bf-a812-b6a7df17e277).</span><span class="sxs-lookup"><span data-stu-id="a5253-118">For details, see [How to: Edit Interop Assemblies](http://msdn.microsoft.com/en-us/16aacb20-2269-42bf-a812-b6a7df17e277).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5253-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a5253-119">Example</span></span>  
 <span data-ttu-id="a5253-120">O código a seguir mostra um exemplo da interface `ISATest` e da classe `SATest` na IDL e os tipos correspondentes no código-fonte C#.</span><span class="sxs-lookup"><span data-stu-id="a5253-120">The following code shows an example of the `ISATest` interface and `SATest` class in IDL and the corresponding types in C# source code.</span></span>  
  
 <span data-ttu-id="a5253-121">**Arquivo IDL ou de biblioteca de tipos**</span><span class="sxs-lookup"><span data-stu-id="a5253-121">**IDL or type library file**</span></span>  
  
```  
 [  
object,  
uuid(40A8C65D-2448-447A-B786-64682CBEF133),  
dual,  
helpstring("ISATest Interface"),  
pointer_default(unique)  
 ]  
interface ISATest : IDispatch  
 {  
[id(1), helpstring("method InSArray")]   
HRESULT InSArray([in] SAFEARRAY(int) *ppsa, [out,retval] int *pSum);  
 };  
 [  
uuid(116CCA1E-7E39-4515-9849-90790DA6431E),  
helpstring("SATest Class")  
 ]  
coclass SATest  
 {  
  [default] interface ISATest;  
 };  
```  
  
 <span data-ttu-id="a5253-122">**Wrapper no código-fonte gerenciado**</span><span class="sxs-lookup"><span data-stu-id="a5253-122">**Wrapper in managed source code**</span></span>  
  
```csharp  
using System;  
using System.Runtime.InteropServices;  
using System.Runtime.CompilerServices;  
  
[assembly:Guid("E4A992B8-6F5C-442C-96E7-C4778924C753")]  
[assembly:ImportedFromTypeLib("SAServerLib")]  
namespace SAServer  
{  
 [ComImport]  
 [Guid("40A8C65D-2448-447A-B786-64682CBEF133")]  
 [TypeLibType(TypeLibTypeFlags.FLicensed)]  
 public interface ISATest  
 {  
  [DispId(1)]  
  //[MethodImpl(MethodImplOptions.InternalCall,  
  // MethodCodeType=MethodCodeType.Runtime)]  
  int InSArray( [MarshalAs(UnmanagedType.SafeArray,  
      SafeArraySubType=VarEnum.VT_I4)] ref int[] param );  
 }   
 [ComImport]  
 [Guid("116CCA1E-7E39-4515-9849-90790DA6431E")]  
 [ClassInterface(ClassInterfaceType.None)]   
 [TypeLibType(TypeLibTypeFlags.FCanCreate)]  
 public class SATest : ISATest   
 {  
  [DispId(1)]  
  [MethodImpl(MethodImplOptions.InternalCall,   
  MethodCodeType=MethodCodeType.Runtime)]  
  extern int ISATest.InSArray( [MarshalAs(UnmanagedType.SafeArray,   
  SafeArraySubType=VarEnum.VT_I4)] ref int[] param );  
 }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="a5253-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a5253-123">See Also</span></span>  
 <span data-ttu-id="a5253-124">[Personalizando RCWs (Runtime Callable Wrappers)](http://msdn.microsoft.com/en-us/4652beaf-77d0-4f37-9687-ca193288c0be) </span><span class="sxs-lookup"><span data-stu-id="a5253-124">[Customizing Runtime Callable Wrappers](http://msdn.microsoft.com/en-us/4652beaf-77d0-4f37-9687-ca193288c0be) </span></span>  
 <span data-ttu-id="a5253-125">[Tipos de dados COM](http://msdn.microsoft.com/en-us/f93ae35d-a416-4218-8700-c8218cc90061) </span><span class="sxs-lookup"><span data-stu-id="a5253-125">[COM Data Types](http://msdn.microsoft.com/en-us/f93ae35d-a416-4218-8700-c8218cc90061) </span></span>  
 <span data-ttu-id="a5253-126">[Como editar assemblies de interoperabilidade](http://msdn.microsoft.com/en-us/16aacb20-2269-42bf-a812-b6a7df17e277) </span><span class="sxs-lookup"><span data-stu-id="a5253-126">[How to: Edit Interop Assemblies](http://msdn.microsoft.com/en-us/16aacb20-2269-42bf-a812-b6a7df17e277) </span></span>  
 <span data-ttu-id="a5253-127">[Resumo da conversão de bibliotecas de tipos em assemblies](http://msdn.microsoft.com/en-us/bf3f90c5-4770-4ab8-895c-3ba1055cc958) </span><span class="sxs-lookup"><span data-stu-id="a5253-127">[Type Library to Assembly Conversion Summary](http://msdn.microsoft.com/en-us/bf3f90c5-4770-4ab8-895c-3ba1055cc958) </span></span>  
 <span data-ttu-id="a5253-128">[Tlbimp.exe (Importador da Biblioteca de Tipos)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) </span><span class="sxs-lookup"><span data-stu-id="a5253-128">[Tlbimp.exe (Type Library Importer)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) </span></span>  
 [<span data-ttu-id="a5253-129">Tlbexp.exe (Exportador de Biblioteca de Tipos)</span><span class="sxs-lookup"><span data-stu-id="a5253-129">Tlbexp.exe (Type Library Exporter)</span></span>](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md)
