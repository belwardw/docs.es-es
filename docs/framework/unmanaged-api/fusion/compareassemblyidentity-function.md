---
title: "CompareAssemblyIdentity (Función)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CompareAssemblyIdentity
api_location:
- fusion.dll
- clr.dll
api_type: COM
f1_keywords: CompareAssemblyIdentity
helpviewer_keywords: CompareAssemblyIdentity function [.NET Framework fusion]
ms.assetid: 8b364ae1-8efa-4744-a7da-81fd093d84d6
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9d9d7b4934d4295ee799fb13d3d749e6b977e644
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="compareassemblyidentity-function"></a><span data-ttu-id="0755e-102">CompareAssemblyIdentity (Función)</span><span class="sxs-lookup"><span data-stu-id="0755e-102">CompareAssemblyIdentity Function</span></span>
<span data-ttu-id="0755e-103">Compara dos identidades de ensamblado para determinar si son equivalentes.</span><span class="sxs-lookup"><span data-stu-id="0755e-103">Compares two assembly identities to determine whether they are equivalent.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0755e-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="0755e-104">Syntax</span></span>  
  
```  
STDAPI CompareAssemblyIdentity (  
    [in]  LPCWSTR                  pwzAssemblyIdentity1,  
    [in]  BOOL                     fUnified1,  
    [in]  LPCWSTR                  pwzAssemblyIdentity2,  
    [in]  BOOL                     fUnified2,  
    [out] BOOL                     *pfEquivalent,  
    [out] AssemblyComparisonResult *pResult  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0755e-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="0755e-105">Parameters</span></span>  
 `pwzAssemblyIdentity1`  
 <span data-ttu-id="0755e-106">[in] Identidad textual del primer ensamblado de la comparación.</span><span class="sxs-lookup"><span data-stu-id="0755e-106">[in] The textual identity of the first assembly in the comparison.</span></span>  
  
 `fUnified1`  
 <span data-ttu-id="0755e-107">[in] Una marca booleana que indica la unificación especificada por el usuario para `pwzAssemblyIdentity1`.</span><span class="sxs-lookup"><span data-stu-id="0755e-107">[in] A Boolean flag that indicates user-specified unification for `pwzAssemblyIdentity1`.</span></span>  
  
 `pwzAssemblyIdentity2`  
 <span data-ttu-id="0755e-108">[in] Identidad textual del segundo ensamblado de la comparación.</span><span class="sxs-lookup"><span data-stu-id="0755e-108">[in] The textual identity of the second assembly in the comparison.</span></span>  
  
 `fUnified2`  
 <span data-ttu-id="0755e-109">[in] Una marca booleana que indica la unificación especificada por el usuario para `pwzAssemblyIdentity2`.</span><span class="sxs-lookup"><span data-stu-id="0755e-109">[in] A Boolean flag that indicates user-specified unification for `pwzAssemblyIdentity2`.</span></span>  
  
 `pfEquivalent`  
 <span data-ttu-id="0755e-110">[out] Una marca booleana que indica si los dos ensamblados son equivalentes.</span><span class="sxs-lookup"><span data-stu-id="0755e-110">[out] A Boolean flag that indicates whether the two assemblies are equivalent.</span></span>  
  
 `pResult`  
 <span data-ttu-id="0755e-111">[out] Un [AssemblyComparisonResult](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md) enumeración que contiene información detallada sobre la comparación.</span><span class="sxs-lookup"><span data-stu-id="0755e-111">[out] An [AssemblyComparisonResult](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md) enumeration that contains detailed information about the comparison.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0755e-112">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="0755e-112">Return Value</span></span>  
 <span data-ttu-id="0755e-113">`pfEquivalent`Devuelve un valor booleano que indica si los dos ensamblados son equivalentes.</span><span class="sxs-lookup"><span data-stu-id="0755e-113">`pfEquivalent` returns a Boolean value that indicates whether the two assemblies are equivalent.</span></span> <span data-ttu-id="0755e-114">`pResult`Devuelve uno de los `AssemblyComparisonResult` valores para dar el motivo más detallado para el valor de `pfEquivalent`.</span><span class="sxs-lookup"><span data-stu-id="0755e-114">`pResult` returns one of the `AssemblyComparisonResult` values, to give a more detailed reason for the value of `pfEquivalent`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0755e-115">Comentarios</span><span class="sxs-lookup"><span data-stu-id="0755e-115">Remarks</span></span>  
 <span data-ttu-id="0755e-116">`CompareAssemblyIdentity`comprueba si `pwzAssemblyIdentity1` y `pwzAssemblyIdentity2` son equivalentes.</span><span class="sxs-lookup"><span data-stu-id="0755e-116">`CompareAssemblyIdentity` checks whether `pwzAssemblyIdentity1` and `pwzAssemblyIdentity2` are equivalent.</span></span> <span data-ttu-id="0755e-117">`pfEquivalent`se establece en `true` en una o varias de las condiciones siguientes:</span><span class="sxs-lookup"><span data-stu-id="0755e-117">`pfEquivalent` is set to `true` under one or more of the following conditions:</span></span>  
  
-   <span data-ttu-id="0755e-118">Las dos identidades de ensamblado son equivalentes.</span><span class="sxs-lookup"><span data-stu-id="0755e-118">The two assembly identities are equivalent.</span></span> <span data-ttu-id="0755e-119">Para los ensamblados con nombre seguro, la equivalencia requiere que el nombre del ensamblado, versión, token de clave pública y la referencia cultural para que sean idénticos.</span><span class="sxs-lookup"><span data-stu-id="0755e-119">For strongly named assemblies, equivalency requires the assembly name, version, public key token, and culture to be identical.</span></span> <span data-ttu-id="0755e-120">Para los ensamblados con nombres simples, equivalencia requiere a una coincidencia en el nombre del ensamblado y la referencia cultural.</span><span class="sxs-lookup"><span data-stu-id="0755e-120">For simply named assemblies, equivalency requires a match on the assembly name and culture.</span></span>  
  
-   <span data-ttu-id="0755e-121">Ambas identidades de ensamblado hacen referencia a ensamblados que se ejecutan en .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0755e-121">Both assembly identities refer to assemblies that run on the .NET Framework.</span></span> <span data-ttu-id="0755e-122">Esta condición devuelve `true` incluso si no coinciden los números de versión de ensamblado.</span><span class="sxs-lookup"><span data-stu-id="0755e-122">This condition returns `true` even if the assembly version numbers do not match.</span></span>  
  
-   <span data-ttu-id="0755e-123">Los dos ensamblados no son ensamblados administrados, pero `fUnified1` o `fUnified2` se estableció en `true`.</span><span class="sxs-lookup"><span data-stu-id="0755e-123">The two assemblies are not managed assemblies, but `fUnified1` or `fUnified2` was set to `true`.</span></span>  
  
 <span data-ttu-id="0755e-124">El `fUnified` marca indica que todos los números de versión hasta el número de versión del ensamblado con nombre seguro se consideran equivalentes al ensamblado con nombre seguro.</span><span class="sxs-lookup"><span data-stu-id="0755e-124">The `fUnified` flag indicates that all version numbers up to the version number of the strongly named assembly are considered equivalent to the strongly named assembly.</span></span> <span data-ttu-id="0755e-125">Por ejemplo, si el valor de `pwzAssemblyIndentity1` es "MyAssembly, versión = 3.0.0.0, culture = neutral, publicKeyToken =..." y el valor de `fUnified1` es `true`, esto indica que todas las versiones de MyAssembly desde la versión 0.0.0.0 hasta la versión 3.0.0.0 deberían se tratan como equivalentes.</span><span class="sxs-lookup"><span data-stu-id="0755e-125">For example, if the value of `pwzAssemblyIndentity1` is "MyAssembly, version=3.0.0.0, culture=neutral, publicKeyToken=....", and the value of `fUnified1` is `true`, this indicates that all versions of MyAssembly from version 0.0.0.0 to 3.0.0.0 should be treated as equivalent.</span></span> <span data-ttu-id="0755e-126">En tal caso, si `pwzAssemblyIndentity2` hace referencia al mismo ensamblado como `pwzAssemblyIndentity1`, salvo que tenga un número de versión menor, `pfEquivalent` está establecido en `true`.</span><span class="sxs-lookup"><span data-stu-id="0755e-126">In such a case, if `pwzAssemblyIndentity2` refers to the same assembly as `pwzAssemblyIndentity1`, except that it has a lower version number, `pfEquivalent` is set to `true`.</span></span> <span data-ttu-id="0755e-127">Si `pwzAssemblyIdentity2` hace referencia a un número de versión mayor, `pfEquivalent` está establecido en `true` sólo si el valor de `fUnified2` es `true`.</span><span class="sxs-lookup"><span data-stu-id="0755e-127">If `pwzAssemblyIdentity2` refers to a higher version number, `pfEquivalent` is set to `true` only if the value of `fUnified2` is `true`.</span></span>  
  
 <span data-ttu-id="0755e-128">El `pResult` parámetro incluye información específica sobre por qué los dos ensamblados se consideran equivalentes o no equivalentes.</span><span class="sxs-lookup"><span data-stu-id="0755e-128">The `pResult` parameter includes specific information about why the two assemblies are considered equivalent or not equivalent.</span></span> <span data-ttu-id="0755e-129">Para obtener más información, consulte [AssemblyComparisonResult (enumeración)](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="0755e-129">For more information, see [AssemblyComparisonResult Enumeration](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0755e-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0755e-130">Requirements</span></span>  
 <span data-ttu-id="0755e-131">**Plataformas:** vea [requisitos del sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0755e-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0755e-132">**Encabezado:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="0755e-132">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="0755e-133">**Biblioteca:** incluye como recurso en MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0755e-133">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0755e-134">**Versiones de .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0755e-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0755e-135">Vea también</span><span class="sxs-lookup"><span data-stu-id="0755e-135">See Also</span></span>  
 [<span data-ttu-id="0755e-136">Funciones estáticas globales de fusión</span><span class="sxs-lookup"><span data-stu-id="0755e-136">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)  
 [<span data-ttu-id="0755e-137">AssemblyComparisonResult (enumeración)</span><span class="sxs-lookup"><span data-stu-id="0755e-137">AssemblyComparisonResult Enumeration</span></span>](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md)