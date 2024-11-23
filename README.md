# DYNAMIC-FORM

import { useState } from "react"
import "./regfrm.css";

export const Regform = () => {
    const[user,setuser] = useState({
        name: "ramkumar",
        email:"you@example.com",
        age :22,
        gender:"male",
        ismarried: true,
        country:"india",
        bio:"write about sopmething",
    })
    function changehandler(e){
        const name = e.target.name;
    // console.log(name)
    const value=e.target.type==="checkbox"?e.target.checked :e.target.value;
    setuser({...user, [name]:value});
    }
    
    return (
        <>
        <table>
            <tbody>
                <tr>
                    <td>Name</td>
                    <td>{user.name}</td>
                </tr>
                <tr>
                    <td>Email</td>
                    <td>{user.email}</td>
                </tr>
                <tr>
                    <td>Age</td>
                    <td>{user.age}</td>
                </tr>
                <tr>
                    <td>Gender</td>
                    <td>{user.gender}</td>
                </tr>
                <tr>
                    <td>Married Status</td>
                    <td>{user.ismarried ? "married" : "notmarried"}</td>
                </tr>
                <tr>
                    <td>country</td>
                    <td>{user.country}</td>
                </tr>
                <tr>
                    <td>bio</td>
                    <td>{user.bio}</td>
                </tr>
            </tbody>
        </table>
        <form>
            <input type="text" placeholder="fullname" name="name" value={user.name} onChange={changehandler} />
            <input type="text" placeholder="you@example.com" name="email"  value={user.email} onChange={changehandler}/>
            <input type="number" placeholder="age" name="age" value={user.age} onChange={changehandler} />
            <div className="gender">
                <label htmlFor="male">
                    <input type="radio" name="gender" id="male"  checked={user.gender == "male"} value="male" onChange={changehandler}  />
                    male
                </label>
                <label htmlFor="female">
                    <input type="radio" name="gender" id="female" checked={user.gender == "female"} value="female" onChange={changehandler}  />
                    female
                </label>
            </div>
            <label htmlFor="ismarried">
                <input type="checkbox" id="ismarried" name="ismarried" checked={user.ismarried} onChange={changehandler}  />
                IsMarried
            </label>
            <div className="select">
                <label htmlFor=" country">Select Country:</label>
                <select name="country" id="country" value={user.country} onChange={changehandler}>
                    <option value="india">india</option>
                    <option value="russia">russia</option>
                    <option value="china">china</option>
                    <option value="uk">uk</option>
                </select>
            </div>
            <textarea name="bio" id="bio" cols="30" rows="5" value={user.bio} placeholder="write about yourself" onChange={changehandler}></textarea>
        </form>
        </>
    )
}
