# Dateinamen & Modularität: Grundpfeiler KI-optimierter Entwicklung  

## 🧠 Kernproblemstellung  
KI-Entwicklungstools analysieren Codekontext selektiv zur Kosteneinsparung. Unklare Dateistrukturen führen zu redundanten Codevorschlägen und Architekturlücken. Systematische Modularisierung wird zum kritischen Erfolgsfaktor.

## 💡 Wirkungsvolle Strategien  

### 📛 Semantische Benennungskonventionen  
- **Domänenbasierte Präfixe**: `payment_processing.go`, `user_analytics.py`  
- **Aktionssuffixe**: `service.go`, `controller.ts`, `repository.py`  
- **Versionskennzeichnung**: `legacy_v1/`, `migration_v2/`  

### 🧩 Modularisierungsprinzipien  
```
src/
├── domain/
│ ├── banking/ # Geschäftslogik
│ └── reporting/
├── infrastructure/
│ ├── database/ # Technische Implementierung
│ └── caching/
└── application/ # Kompositionsschicht
```

### 🔍 Kontextsteuerung für KI  
- **Datei-Metadaten**:  
```
payment_service.go
responsibility: "Transaction processing core logic"
dependencies: [currency_lib, audit_trail]
changed_last: 2024-03-15
```

## 🚧 Typische Fallstricke  

### ❌ Generische Sammeldateien  
- `utils.py` → `geospatial_calculations.py`  
- `helpers.ts` → `jwt_token_manager.ts`  

### ❌ Cross-Domain-Kontamination  
```
payment_invoice_controller.db_connector.go

payment/controller_invoice.go

infrastructure/database/postgres.go
```

### ❌ Implizite Abhängigkeiten  
- **Problem**:  
  `reporting_service` nutzt versteckte Funktionen aus `legacy/old_calc.py`  
- **Lösung**:  
reporting/requirements.txt
explicit_dependencies = ["finance@1.2.3"]

## ⚙️ Implementierungsleitfaden  

### 1. Architektur-Impact-Analyse  
```
npx modularity-checker --threshold 0.85 \
--rule "Max 3 Verantwortlichkeiten pro Datei"
```

### 2. KI-gestützte Refactoring  
Vorschlag für bessere Struktur
```
ai-refactor --input src/ --strategy domain-driven
```

### 3. Kontext-Enforcement  
```
.aicoderules
file_naming:
pattern: "^[a-z]+_[a-z]+(_v\d+)?.[a-z]+$"
forbidden: ["util", "misc", "general"]
```

## 📈 Auswirkungsmetriken  

| Faktor               | Vorher | Nachher |  
|----------------------|--------|---------|  
| Code-Duplikation     | 38%    | 9%      |  
| KI-Fehlerquote       | 41%    | 12%     |  
| Dev-Onboarding-Zeit  | 16h    | 4h      |  

## 🔄 Evolutionärer Ansatz  

1. **Automated Tagging**  
```
def auto_tag(file_content):
return NLPClassifier.predict_module_type(file_content)
```

2. **Dynamic Context Windowing**  
```
AI.setContextStrategy({
fileProximity: 3,
importHierarchy: true
})
```

3. **Semantic Search Integration**  
```
code-search --query "currency conversion"
--filter "domain/finance"
```