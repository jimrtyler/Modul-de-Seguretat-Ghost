# 👻 Mòdul de Seguretat Ghost
**Eina d'Enduriment de Seguretat de Windows i Azure basada en PowerShell**

> **Enduriment proactiu de seguretat per a punts finals de Windows i entorns Azure.** Ghost proporciona funcions d'enduriment basades en PowerShell que poden ajudar a reduir vectors d'atac comuns desactivant serveis i protocols innecessaris.

## ⚠️ Renúncies Importants

**ES REQUEREIX PROVES**: Proveu sempre Ghost primer en entorns no productius. Desactivar serveis pot afectar funcions de negoci legítimes.

**CAP GARANTIA**: Tot i que Ghost s'orienta a vectors d'atac comuns, cap eina de seguretat pot prevenir tots els atacs. Aquest és un component d'una estratègia de seguretat integral.

**IMPACTE OPERACIONAL**: Algunes funcions poden afectar la funcionalitat del sistema. Reviseu cada configuració acuradament abans del desplegament.

**AVALUACIÓ PROFESSIONAL**: Per a entorns de producció, consulteu amb especialistes en seguretat per assegurar que les configuracions s'alineïn amb les necessitats de la vostra organització.

## 📊 El Panorama de Seguretat

Els danys per ransomware van arribar als **57 mil milions de dòlars el 2025**, amb investigacions que indiquen que molts atacs exitosos exploten serveis bàsics de Windows i configuracions incorrectes. Els vectors d'atac comuns inclouen:

- **El 90% dels incidents de ransomware** involucren explotació d'RDP
- **Les vulnerabilitats d'SMBv1** van permetre atacs com WannaCry i NotPetya
- **Els macros de documents** romanen com a mètode primari de lliurament de malware
- **Els atacs basats en USB** continuen dirigint-se a xarxes aïllades de l'aire
- **L'abús de PowerShell** ha augmentat significativament en els darrers anys

## 🛡️ Funcions de Seguretat de Ghost

Ghost proporciona **16 funcions d'enduriment de Windows** més **integració de seguretat Azure**:

### Enduriment de Punts Finals de Windows

| Funció | Propòsit | Consideracions |
|--------|----------|----------------|
| `Set-RDP` | Gestiona l'accés a l'escriptori remot | Pot impactar l'administració remota |
| `Set-SMBv1` | Controla el protocol SMB legacy | Requerit per sistemes molt antics |
| `Set-AutoRun` | Controla AutoPlay/AutoRun | Pot afectar la conveniència de l'usuari |
| `Set-USBStorage` | Restringeix dispositius d'emmagatzematge USB | Pot afectar l'ús legítim d'USB |
| `Set-Macros` | Controla l'execució de macros d'Office | Pot afectar documents amb macros habilitats |
| `Set-PSRemoting` | Gestiona la connexió remota de PowerShell | Pot afectar la gestió remota |
| `Set-WinRM` | Controla Windows Remote Management | Pot afectar l'administració remota |
| `Set-LLMNR` | Gestiona el protocol de resolució de noms | Generalment segur per desactivar |
| `Set-NetBIOS` | Controla NetBIOS sobre TCP/IP | Pot afectar aplicacions legacy |
| `Set-AdminShares` | Gestiona comparticions administratives | Pot afectar l'accés remot a fitxers |
| `Set-Telemetry` | Controla la recollida de dades | Pot afectar capacitats de diagnòstic |
| `Set-GuestAccount` | Gestiona el compte convidat | Generalment segur per desactivar |
| `Set-ICMP` | Controla respostes ping | Pot afectar el diagnòstic de xarxa |
| `Set-RemoteAssistance` | Gestiona l'assistència remota | Pot afectar operacions d'help desk |
| `Set-NetworkDiscovery` | Controla el descobriment de xarxa | Pot afectar la navegació de xarxa |
| `Set-Firewall` | Gestiona Windows Firewall | Crític per a la seguretat de xarxa |

### Seguretat Azure Cloud

| Funció | Propòsit | Requisits |
|--------|----------|-----------|
| `Set-AzureSecurityDefaults` | Habilita seguretat bàsica d'Azure AD | Permisos de Microsoft Graph |
| `Set-AzureConditionalAccess` | Configura polítiques d'accés | Llicències Azure AD P1/P2 |
| `Set-AzurePrivilegedUsers` | Audita comptes privilegiats | Permisos Global Admin |

### Opcions de Desplegament Empresarial

| Mètode | Cas d'Ús | Requisits |
|--------|-----------|-----------|
| **Execució Directa** | Proves, entorns petits | Drets d'admin locals |
| **Group Policy** | Entorns de domini | Admin de domini, gestió GP |
| **Microsoft Intune** | Dispositius gestionats al núvol | Llicències Intune, Graph API |

## 🚀 Inici Ràpid

### Avaluació de Seguretat
```powershell
# Carregueu el mòdul Ghost
IEX(Invoke-WebRequest 'https://raw.githubusercontent.com/jimrtyler/Ghost/main/Ghost.ps1')

# Comproveu la postura de seguretat actual
Get-Ghost
```

### Enduriment Bàsic (Proveu Primer)
```powershell
# Enduriment essencial - proveu primer en entorn de laboratori
Set-Ghost -SMBv1 -AutoRun -Macros

# Reviseu els canvis
Get-Ghost
```

### Desplegament Empresarial
```powershell
# Desplegament Group Policy (entorns de domini)
Set-Ghost -SMBv1 -AutoRun -GroupPolicy

# Desplegament Intune (dispositius gestionats al núvol)
Set-Ghost -SMBv1 -RDP -USBStorage -Intune
```

## 📋 Mètodes d'Instal·lació

### Opció 1: Descàrrega Directa (Proves)
```powershell
IEX(Invoke-WebRequest 'https://raw.githubusercontent.com/jimrtyler/Ghost/main/Ghost.ps1')
```

### Opció 2: Instal·lació de Mòdul
```powershell
# Instal·leu des de PowerShell Gallery (quan estigui disponible)
Install-Module Ghost -Scope CurrentUser
Import-Module Ghost
```

### Opció 3: Desplegament Empresarial
```powershell
# Copieu a la ubicació de xarxa per al desplegament Group Policy
# Configureu scripts PowerShell d'Intune per al desplegament al núvol
```

## 💼 Exemples de Casos d'Ús

### Petit Negoci
```powershell
# Protecció bàsica amb impacte mínim
Set-Ghost -SMBv1 -AutoRun -Macros -ICMP
```

### Entorn Sanitari
```powershell
# Enduriment centrat en HIPAA
Set-Ghost -SMBv1 -RDP -USBStorage -AdminShares -Telemetry
```

### Serveis Financers
```powershell
# Configuració d'alta seguretat
Set-Ghost -RDP -SMBv1 -AutoRun -USBStorage -Macros -PSRemoting -AdminShares
```

### Organització Cloud-First
```powershell
# Desplegament gestionat per Intune
Connect-IntuneGhost -Interactive
Set-Ghost -SMBv1 -RDP -AutoRun -Macros -Intune
```

## 🔍 Detalls de Funcions

### Funcions Principals d'Enduriment

#### Serveis de Xarxa
- **RDP**: Bloqueja l'accés a l'escriptori remot o aleatoritza el port
- **SMBv1**: Desactiva el protocol de compartició de fitxers legacy
- **ICMP**: Prevé respostes ping per al reconeixement
- **LLMNR/NetBIOS**: Bloqueja protocols de resolució de noms legacy

#### Seguretat d'Aplicacions
- **Macros**: Desactiva l'execució de macros en aplicacions Office
- **AutoRun**: Prevé l'execució automàtica des de mitjans extraïbles

#### Gestió Remota
- **PSRemoting**: Desactiva sessions remotes de PowerShell
- **WinRM**: Atura Windows Remote Management
- **Remote Assistance**: Bloqueja connexions d'assistència remota

#### Control d'Accés
- **Admin Shares**: Desactiva comparticions C$, ADMIN$
- **Guest Account**: Desactiva l'accés del compte convidat
- **USB Storage**: Restringeix l'ús de dispositius USB

### Integració Azure
```powershell
# Connecteu al tenant Azure
Connect-AzureGhost -Interactive

# Habiliteu els valors per defecte de seguretat
Set-AzureSecurityDefaults -Enable

# Configureu l'accés condicional
Set-AzureConditionalAccess -BlockLegacyAuth -RequireMFA

# Auditeu usuaris privilegiats
Set-AzurePrivilegedUsers -AuditOnly
```

### Integració Intune (Nou a v2)
```powershell
# Connecteu a Intune
Connect-IntuneGhost -Interactive

# Desplegueu via polítiques Intune
Set-IntuneGhost -Settings @{
    RDP = $true
    SMBv1 = $true
    USBStorage = $true
    Macros = $true
}
```

## ⚠️ Consideracions Importants

### Requisits de Proves
- **Entorn de Laboratori**: Proveu totes les configuracions primer en un entorn aïllat
- **Desplegament Gradual**: Desplegueu gradualment per identificar problemes
- **Pla de Rollback**: Assegureu-vos que podeu revertir canvis si cal
- **Documentació**: Registreu quines configuracions funcionen per al vostre entorn

### Impacte Potencial
- **Productivitat de l'Usuari**: Algunes configuracions poden afectar els fluxos de treball diaris
- **Aplicacions Legacy**: Els sistemes més antics poden requerir certs protocols
- **Accés Remot**: Considereu l'impacte en l'administració remota legítima
- **Processos de Negoci**: Verifiqueu que les configuracions no trenquin funcions crítiques

### Limitacions de Seguretat
- **Defensa en Profunditat**: Ghost és una capa de seguretat, no una solució completa
- **Gestió Contínua**: La seguretat requereix monitorització i actualitzacions contínues
- **Formació d'Usuaris**: Els controls tècnics han d'anar aparellats amb consciència de seguretat
- **Evolució d'Amenaces**: Nous mètodes d'atac poden superar la protecció actual

## 🎯 Escenaris d'Atac d'Exemple

Mentre Ghost s'orienta a vectors d'atac comuns, la prevenció específica depèn de la implementació i proves adequades:

### Atacs Estil WannaCry
- **Mitigació**: `Set-Ghost -SMBv1` desactiva el protocol vulnerable
- **Consideració**: Assegureu-vos que cap sistema legacy requereixi SMBv1

### Ransomware Basat en RDP
- **Mitigació**: `Set-Ghost -RDP` bloqueja l'accés a l'escriptori remot
- **Consideració**: Pot requerir mètodes alternatius d'accés remot

### Malware Basat en Documents
- **Mitigació**: `Set-Ghost -Macros` desactiva l'execució de macros
- **Consideració**: Pot afectar documents legítims amb macros habilitats

### Amenaces Lliurades per USB
- **Mitigació**: `Set-Ghost -USBStorage -AutoRun` restringeix la funcionalitat USB
- **Consideració**: Pot afectar l'ús legítim de dispositius USB

## 🏢 Característiques Empresarials

### Suport Group Policy
```powershell
# Apliqueu configuracions via registre Group Policy
Set-Ghost -SMBv1 -RDP -AutoRun -GroupPolicy

# Les configuracions s'apliquen a tot el domini després del refresc GP
gpupdate /force
```

### Integració Microsoft Intune
```powershell
# Creeu polítiques Intune per a configuracions Ghost
Set-IntuneGhost -Settings $GhostSettings -Interactive

# Les polítiques es despleguen automàticament als dispositius gestionats
```

### Informes de Compliment
```powershell
# Genereu informe d'avaluació de seguretat
Get-Ghost | Export-Csv -Path "SecurityAudit-$(Get-Date -Format 'yyyy-MM-dd').csv"

# Informe de postura de seguretat Azure
Get-AzureGhost | Out-File "AzureSecurityReport.txt"
```

## 📚 Millors Pràctiques

### Pre-Desplegament
1. **Documenteu l'Estat Actual**: Executeu `Get-Ghost` abans dels canvis
2. **Proveu Exhaustivament**: Valideu en entorn no productiu
3. **Planifiqueu el Rollback**: Sabeu com revertir cada configuració
4. **Revisió de Parts Interessades**: Assegureu-vos que les unitats de negoci aprovin els canvis

### Durant el Desplegament
1. **Enfocament Gradual**: Desplegueu primer als grups pilot
2. **Monitoritzeu l'Impacte**: Vigileu les queixes d'usuaris o problemes del sistema
3. **Documenteu Problemes**: Registreu qualsevol problema per a referència futura
4. **Comuniqueu Canvis**: Informeu els usuaris sobre millores de seguretat

### Post-Desplegament
1. **Avaluació Regular**: Executeu periòdicament `Get-Ghost` per verificar configuracions
2. **Actualitzeu Documentació**: Mantingueu les configuracions de seguretat actualitzades
3. **Reviseu l'Efectivitat**: Monitoritzeu per incidents de seguretat
4. **Millora Contínua**: Ajusteu configuracions basant-vos en el panorama d'amenaces

## 🔧 Resolució de Problemes

### Problemes Comuns
- **Errors de Permisos**: Assegureu-vos d'una sessió PowerShell elevada
- **Dependències de Serveis**: Alguns serveis poden tenir dependències
- **Compatibilitat d'Aplicacions**: Proveu amb aplicacions de negoci
- **Connectivitat de Xarxa**: Verifiqueu que l'accés remot encara funcioni

### Opcions de Recuperació
```powershell
# Rehabiliteu serveis específics quan calgui
Set-RDP -Enable
Set-SMBv1 -Enable
Set-AutoRun -Enable
Set-Macros -Enable
```

## 👨‍💻 Sobre l'Autor

**Jim Tyler** - Microsoft MVP per a PowerShell
- **YouTube**: [@PowerShellEngineer](https://youtube.com/@PowerShellEngineer) (10.000+ subscriptors)
- **Butlletí**: [PowerShell.News](https://powershell.news) - Intel·ligència de seguretat setmanal
- **Autor**: "PowerShell for Systems Engineers"
- **Experiència**: Dècades d'automatització PowerShell i seguretat Windows

## 📄 Llicència i Renúncia

### Llicència MIT
Ghost es proporciona sota la Llicència MIT per a ús, modificació i distribució gratuïts.

### Renúncia de Seguretat
- **Cap Garantia**: Ghost es proporciona "tal com és" sense garantia de cap tipus
- **Proves Requerides**: Proveu sempre primer en entorns no productius
- **Orientació Professional**: Consulteu especialistes en seguretat per a desplegaments de producció
- **Impacte Operacional**: Els autors no són responsables de cap interrupció operacional
- **Seguretat Integral**: Ghost és un component d'una estratègia de seguretat completa

### Suport
- **Problemes GitHub**: [Informeu d'errors o sol·liciteu característiques](https://github.com/jimrtyler/Ghost/issues)
- **Documentació**: Useu `Get-Help <function> -Full` per ajuda detallada
- **Comunitat**: Fòrums de la comunitat PowerShell i seguretat

---

**🔐 Enfortiu la vostra postura de seguretat amb Ghost - però proveu sempre primer.**

```powershell
# Comenceu amb avaluació, no amb suposicions
Get-Ghost
```

**⭐ Afegiu una estrella a aquest repositori si Ghost ajuda a millorar la vostra postura de seguretat!**