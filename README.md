# classFiles
# Controller
``` C#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Web;
using System.Web.Mvc;
using _05._10._2017.Models;

namespace _05._10._2017.Controllers
{
    
    public class UserController : Controller
    {
        private UserEntities db = new UserEntities();
        // GET: User
        public ActionResult Index()
        {
            return View(db.Users.ToList());
        }
        public ActionResult Delete()
        {
            return View();
        }
        [HttpGet]
        public ActionResult Create()
        {
            return View();
        }
        [HttpPost]
        public ActionResult Create(FormCollection user)
        {
            User myUser = user as User;
            db.Users.Add(user);
            db.SaveChanges();
            return RedirectToAction("Index");
        }
    }
}
```
# View (Create)
``` C#

@{
    ViewBag.Title = "Create";
    Layout = "~/Views/Shared/_Layout.cshtml";
}

<h2>Create</h2>
@using (Html.BeginForm("Create", "User", FormMethod.Post))
{
    <div class="form-group">
        <label for="name">Id:</label>
        <input type="number" class="form-control" name="id" id="id">
    </div>
    <div class="form-group">
        <label for="name">Name:</label>
        <input type="text" class="form-control" name="name" id="name">
    </div>
    <div class="form-group">
        <label for="surname">Surname:</label>
        <input type="text" class="form-control" name="surname" id="surname">
    </div>
    <div class="form-group">
        <label for="comment">Comment:</label>
        <textarea type="text" class="form-control" name="comment" id="comment"></textarea>
    </div>
    <div class="form-group">
        <input type="submit" class="form-control" name="submit" id="submit" value="Add User">
    </div>
}


```
