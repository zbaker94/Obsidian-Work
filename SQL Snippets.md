
### Roles
```SQL
  
  --Warrant as LEO

  UPDATE GenericCourt.GenericCourt.Staff

  SET StaffTypeID = (

		SELECT StaffTypeID

		FROM GenericCourt.GenericCourt.StaffType

		WHERE Name = 'LawEnforcement'),

	StateMachineID = (

		SELECT StateMachineID

		FROM GenericCourt.GenericCourt.StateMachine

		WHERE Name = 'Law Enforcement'),

	RoleID = (

		SELECT RoleID

		FROM GenericCourt.GenericCourt.Role

		WHERE Name = 'Law Enforcement Officer')

  WHERE Email = 'kevin.moore@claytoncountyga.gov'

​

​

  --Warrarnt as LEO Supervisor

    UPDATE GenericCourt.GenericCourt.Staff

  SET StaffTypeID = (

		SELECT StaffTypeID

		FROM GenericCourt.GenericCourt.StaffType

		WHERE Name = 'LawEnforcement'),

	StateMachineID = (

		SELECT StateMachineID

		FROM GenericCourt.GenericCourt.StateMachine

		WHERE Name = 'Law Enforcement'),

	RoleID = (

		SELECT RoleID

		FROM GenericCourt.GenericCourt.Role

		WHERE Name = 'Law Enforcement Supervisor')

  WHERE Email = 'kevin.moore@claytoncountyga.gov'

​

​

  --Magistrate as Judge

  UPDATE GenericCourt.GenericCourt.Staff

  SET StaffTypeID = (

		SELECT StaffTypeID

		FROM GenericCourt.GenericCourt.StaffType

		WHERE Name = 'Judge'),

	StateMachineID = (

		SELECT StateMachineID

		FROM GenericCourt.GenericCourt.StateMachine

		WHERE Name = 'Magistrate Court'),

	RoleID = (

		SELECT RoleID

		FROM GenericCourt.GenericCourt.Role

		WHERE Name = 'Judge')

  WHERE Email = 'kevin.moore@claytoncountyga.gov'

​

​

  --Magistrate as Judicial Assistant

  UPDATE GenericCourt.GenericCourt.Staff

  SET StaffTypeID = (

		SELECT StaffTypeID

		FROM GenericCourt.GenericCourt.StaffType

		WHERE Name = 'Clerk'),

	StateMachineID = (

		SELECT StateMachineID

		FROM GenericCourt.GenericCourt.StateMachine

		WHERE Name = 'Magistrate Court'),

	RoleID = (

		SELECT RoleID

		FROM GenericCourt.GenericCourt.Role

		WHERE Name = 'Judicial Assistant')

  WHERE Email = 'kevin.moore@claytoncountyga.gov'

​

  --Warrant as Intake Clerk

  UPDATE GenericCourt.GenericCourt.Staff

  SET StaffTypeID = (

		SELECT StaffTypeID

		FROM GenericCourt.GenericCourt.StaffType

		WHERE Name = 'LawEnforcement'),

	StateMachineID = (

		SELECT StateMachineID

		FROM GenericCourt.GenericCourt.StateMachine

		WHERE Name = 'Law Enforcement'),

	RoleID = (

		SELECT RoleID

		FROM GenericCourt.GenericCourt.Role

		WHERE Name = 'Intake or Classification Clerk')

  WHERE Email = 'kevin.moore@claytoncountyga.gov'

​

​

  --Warrant as Jail Supervisor

  UPDATE GenericCourt.GenericCourt.Staff

  SET StaffTypeID = (

		SELECT StaffTypeID

		FROM GenericCourt.GenericCourt.StaffType

		WHERE Name = 'LawEnforcement'),

	StateMachineID = (

		SELECT StateMachineID

		FROM GenericCourt.GenericCourt.StateMachine

		WHERE Name = 'Law Enforcement'),

	RoleID = (

		SELECT RoleID

		FROM GenericCourt.GenericCourt.Role

		WHERE Name = 'Jail Supervisor')

  WHERE Email = 'kevin.moore@claytoncountyga.gov'

​

​

  --Warrant as Deputy Officer

  UPDATE GenericCourt.GenericCourt.Staff

  SET StaffTypeID = (

		SELECT StaffTypeID

		FROM GenericCourt.GenericCourt.StaffType

		WHERE Name = 'LawEnforcement'),

	StateMachineID = (

		SELECT StateMachineID

		FROM GenericCourt.GenericCourt.StateMachine

		WHERE Name = 'Law Enforcement'),

	RoleID = (

		SELECT RoleID

		FROM GenericCourt.GenericCourt.Role

		WHERE Name = 'Deputy Officer')

  WHERE Email = 'kevin.moore@claytoncountyga.gov'

​

​

  --Offense Curation

  UPDATE GenericCourt.GenericCourt.Staff

  SET StateMachineID = (

		SELECT StateMachineID

		FROM GenericCourt.GenericCourt.StateMachine

		WHERE Name = 'Offense Curation')

  WHERE Email = 'kevin.moore@claytoncountyga.gov'

​

​

  --Handoff: Superior Court

  UPDATE GenericCourt.GenericCourt.Staff

  SET StateMachineID = (

		SELECT StateMachineID

		FROM GenericCourt.GenericCourt.StateMachine

		WHERE Name = 'Superior Court')

  WHERE Email = 'kevin.moore@claytoncountyga.gov'

​

​

  --Handoff: State Court

  UPDATE GenericCourt.GenericCourt.Staff

  SET StateMachineID = (

		SELECT StateMachineID

		FROM GenericCourt.GenericCourt.StateMachine

		WHERE Name = 'State Court')

  WHERE Email = 'kevin.moore@claytoncountyga.gov'

​

​

  --Handoff: District Attorney

  UPDATE GenericCourt.GenericCourt.Staff

  SET StateMachineID = (

		SELECT StateMachineID

		FROM GenericCourt.GenericCourt.StateMachine

		WHERE Name = 'District Attorney')

  WHERE Email = 'kevin.moore@claytoncountyga.gov'

​

​

  --Handoff: Solicitor General

  UPDATE GenericCourt.GenericCourt.Staff

  SET StateMachineID = (

		SELECT StateMachineID

		FROM GenericCourt.GenericCourt.StateMachine

		WHERE Name = 'Solicitor General')

  WHERE Email = 'kevin.moore@claytoncountyga.gov'

​

​

  --Handoff: Magistrate Clerk

  UPDATE GenericCourt.GenericCourt.Staff

  SET StateMachineID = (

		SELECT StateMachineID

		FROM GenericCourt.GenericCourt.StateMachine

		WHERE Name = 'Magistrate Clerk')

  WHERE Email = 'kevin.moore@claytoncountyga.gov'

​

​

  --Handoff: Sheriff Warrant

  UPDATE GenericCourt.GenericCourt.Staff

  SET StateMachineID = (

		SELECT StateMachineID

		FROM GenericCourt.GenericCourt.StateMachine

		WHERE Name = 'Sheriff Warrant')

  WHERE Email = 'kevin.moore@claytoncountyga.gov'

​

​

  --Handoff: Sheriff Classification

  UPDATE GenericCourt.GenericCourt.Staff

  SET StateMachineID = (

		SELECT StateMachineID

		FROM GenericCourt.GenericCourt.StateMachine

		WHERE Name = 'Sheriff Classification')

  WHERE Email = 'kevin.moore@claytoncountyga.gov'
```