# Ifemi
Site de amor
Action: file_editor str_replace /app/frontend/src/App.js --old-str "import { useEffect } from \"react\";
import \"./App.css\";
import { BrowserRouter, Routes, Route } from \"react-router-dom\";
import axios from \"axios\";

const BACKEND_URL = process.env.REACT_APP_BACKEND_URL;
const API = `${BACKEND_URL}/api`;

const Home = () => {
  const helloWorldApi = async () => {
    try {
      const response = await axios.get(`${API}/`);
      console.log(response.data.message);
    } catch (e) {
      console.error(e, `errored out requesting / api`);
    }
  };

  useEffect(() => {
    helloWorldApi();
  }, []);

  return (
    <div>
      <header className=\"App-header\">
        <a
          className=\"App-link\"
          href=\"https://emergent.sh\"
          target=\"_blank\"
          rel=\"noopener noreferrer\"
        >
          <img src=\"https://avatars.githubusercontent.com/in/1201222?s=120&u=2686cf91179bbafbc7a71bfbc43004cf9ae1acea&v=4\" />
        </a>
        <p className=\"mt-5\">Building something incredible ~!</p>
      </header>
    </div>
  );
};

function App() {
  return (
    <div className=\"App\">
      <BrowserRouter>
        <Routes>
          <Route path=\"/\" element={<Home />}>
            <Route index element={<Home />} />
          </Route>
        </Routes>
      </BrowserRouter>
    </div>
  );
}" --new-str "import React from \"react\";
import \"./App.css\";
import { BrowserRouter, Routes, Route } from \"react-router-dom\";
import AdminPanel from \"./components/AdminPanel\";
import CouplePage from \"./components/CouplePage\";
import { Toaster } from \"sonner\";

function App() {
  return (
    <div className=\"App\">
      <BrowserRouter>
        <Routes>
          <Route path=\"/\" element={<AdminPanel />} />
          <Route path=\"/admin\" element={<AdminPanel />} />
          <Route path=\"/couple/:uniqueLink\" element={<CouplePage />} />
        </Routes>
      </BrowserRouter>
      <Toaster position=\"top-center\" />
    </div>
  );
}"
Observation: Excellent! The file has been successfully updated. The changes include:

1. **Removed** the old imports (`useEffect`, `axios`) and API-related code
2. **Added** new imports for `AdminPanel`, `CouplePage`, and `Toaster` from `sonner`
3. **Replaced** the routing structure with new routes:
   - `/` → AdminPanel
   - `/admin` → AdminPanel  
   - `/couple/:uniqueLink` → CouplePage
4. **Added** the Toaster component for notifications
5. **Removed** the old Home component and its API call logic

The App.js file has been transformed from a simple hello-world application to a proper routing structure for what appears to be a couples/admin management application.
 Summary: ## App.js Routing Update Complete
- Successfully replaced the basic hello-world App.js with proper routing structure
- Added routes for AdminPanel (/, /admin) and CouplePage (/couple/:uniqueLink)
- Integrated Toaster component from sonner for notifications
- Removed old API calling logic and simplified the component structure
Here is the diff:
diff --git a/frontend/src/App.js b/frontend/src/App.js
index 3ece752..ab9a1c9 100644
--- a/frontend/src/App.js
+++ b/frontend/src/App.js
@@ -1,52 +1,21 @@
-import { useEffect } from "react";
-import "@/App.css";
+import React from "react";
+import "./App.css";
 import { BrowserRouter, Routes, Route } from "react-router-dom";
-import axios from "axios";
-
-const BACKEND_URL = process.env.REACT_APP_BACKEND_URL;
-const API = `${BACKEND_URL}/api`;
-
-const Home = () => {
-  const helloWorldApi = async () => {
-    try {
-      const response = await axios.get(`${API}/`);
-      console.log(response.data.message);
-    } catch (e) {
-      console.error(e, `errored out requesting / api`);
-    }
-  };
-
-  useEffect(() => {
-    helloWorldApi();
-  }, []);
-
-  return (
-    <div>
-      <header className="App-header">
-        <a
-          className="App-link"
-          href="https://emergent.sh"
-          target="_blank"
-          rel="noopener noreferrer"
-        >
-          <img src="https://avatars.githubusercontent.com/in/1201222?s=120&u=2686cf91179bbafbc7a71bfbc43004cf9ae1acea&v=4" />
-        </a>
-        <p className="mt-5">Building something incredible ~!</p>
-      </header>
-    </div>
-  );
-};
+import AdminPanel from "./components/AdminPanel";
+import CouplePage from "./components/CouplePage";
+import { Toaster } from "sonner";
 
 function App() {
   return (
     <div className="App">
       <BrowserRouter>
         <Routes>
-          <Route path="/" element={<Home />}>
-            <Route index element={<Home />} />
-          </Route>
+          <Route path="/" element={<AdminPanel />} />
+          <Route path="/admin" element={<AdminPanel />} />
+          <Route path="/couple/:uniqueLink" element={<CouplePage />} />
         </Routes>
       </BrowserRouter>
+      <Toaster position="top-center" />
     </div>
   );
 }